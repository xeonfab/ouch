# Rectification-achats-v2 — period-correction bundling and UX fixes (2026-08-26)

Author: Claude (acting as prototype engineer for Fabien Riou), summarizing implementation work carried out in the `agicap-prototypes` repo, prototype `rectification-achats-v2`, across a single continuous working session.

## Part 1 — Atelier 24/08 decisions + targeted UX fixes

### Status model: Transmis vs Accepté

`transmit()` now sets the reporting to an intermediate `transmitted` status rather than jumping straight to `accepted` — the prototype no longer conflates "sent to the DGFiP" with "accepted by the DGFiP". `STATUS_LABEL`/`STATUS_COLOR` updated: `to-rectify` → "À transmettre" (renamed from "À rectifier") / caution color; `transmitted` → "Transmis" / primary color; `accepted` → "Accepté" / success color.

### Deletion / restoration lifecycle

- Deleting an invoice from an already-transmitted reporting creates or completes a rectificatif; deleting from within a rectificatif directly tags the line "Supprimé" without a confirmation dialog.
- A new "Annuler la suppression" action on the invoice drawer restores a deleted line back to "Inchangé".
- `pruneIfFullyUnchanged()`: when every line of a rectificatif reverts to "Inchangé" (e.g. a deletion undone), the rectificatif is deleted automatically and the user is redirected to the **original** reporting it was correcting (`sourceReportingId`), not to the Historique list — fixed after Fabien caught the wrong redirect target during manual testing.
- Bulk selection now correctly excludes and explicitly signals both already-deleted lines and pré-comptabilité-locked lines (previously only one of the two exclusions was handled, and only for ventes — achats bulk selection was fixed to work the same way).

### List/table polish

- Pagination added to both "À transmettre" and "Historique" pages (`flipper-pagination` as a sibling after `flipper-data-table` — `FlipperFooterRowDirective` documented by the Flipper MCP was not actually present in the installed package version).
- Historique: Statut column restored, "Régime de TVA" column removed.
- Mock invoice volume padded to ~30 lines per reporting for more realistic manual testing (`padInvoices()` filler generator).

### Transmit confirmation dialog

Recap simplified to a caution banner plus a single horizontal `flipper-description-list` (Entité, Type, Période, SIREN, Raison sociale, Total TVA). The confirm button color was changed from red (`warn`) to blue (`primary`, via `type: 'information'` on the dialog) per Fabien's feedback that the destructive-looking red was undermining trust in a routine, expected action.

### Deploy

This batch was deployed as PR #346, including a same-session fix for a `flowType` copy-paste bug in the filler-invoice generator (flagged by the repo's security bot) and a git-history correction after an unrelated `wiki-visualizer` manifest entry was accidentally swept into the fix commit.

## Part 2 — Period-correction bundling (the substantial new mechanism)

### The problem

A "correction de période" — an invoice's issue date corrected such that it moves from one declared VAT period to another — always produces **two rectificatifs**: an annule/remplace on the old period (removing the invoice) and a new/updated reporting on the new period (adding it). If these two are transmitted to the DGFiP independently and out of sync, the same invoice can end up declared as present in two periods simultaneously — a duplicate-declaration risk with the tax administration.

This is not a new discovery: the squad's 2026-08-20 sync had already decided to block cross-period corrections entirely upstream (in SIM/AP) for V1, specifically to sidestep this exact risk — a pragmatic "move fast" choice, not a permanent architectural answer. This session picked up the open question of what the **target-vision** (post-V1) solution should look like, once cross-period correction eventually needs to be supported (e.g. once Public API/V2 sources are in scope — the existing "Cartographie des tâches" doc already described a 2-rectificatifs mechanic as active for Public API, just not surfaced in UI).

### Recommendation discussed

Rather than relying on the user to remember to transmit both halves in the right order, treat the linked pair (or group) as **one user-facing transmission action**: bundle both files into a single "Transmettre" click, in the correct backend order (removal first, addition second), with a backend-side safety net (never dispatch the "addition" file until the "removal" file is confirmed accepted) for cases where the UI-level guarantee alone isn't enough (e.g. a future automated batch-transmission path).

### Prototype build — iterative, driven by direct feedback

1. **First pass**: an info banner on the reporting that *receives* the moved invoice ("nouvelle période"), linking to the sibling rectificatif; the *losing* side ("ancienne période") deliberately showed nothing, on Fabien's explicit call — a banner firing on every invoice move would add noise for no benefit.
2. **Confirmation dialog became a genuine "grouped" transmission**: clicking "Transmettre" on either linked reporting opens a single recap covering both periods, and confirming transmits both in one action (`ReportingService.transmit()` called for each id) rather than requiring two separate manual transmissions.
3. **Wording pass** (via the UX-writing skill): fixed a grammatically ambiguous banner ("provient d'une correction de période depuis X" mixed two constructions), shortened the modal's caution banner text.
4. **Modal redesign, round 1**: moved from generic period-level totals to listing the actually-moved invoice(s), framed in a bordered box, separated from the description-lists above.
5. **Pluralization fix**: the banner assumed exactly one invoice moved; changed to count-aware wording ("Facture déplacée" / "N factures déplacées").
6. **Symmetric banners**: added the previously-missing banner on the "ancienne période" side too, so both linked reportings surface the link and a shortcut into the transmission preview — but constrained to **one button per banner** (the Flipper `flipper-banner` DS component's documented stories never show two action buttons on the same banner; the earlier two-button layout visually broke, buttons overflowing the banner's colored area).
7. **Modal redesign, round 2**: restructured around the invoice as the unique anchor (number + supplier + amount, shown once) rather than duplicating the same invoice under both a "removed" and an "added" block — the duplication read as a bug ("doublon de la même facture") even though it was intentional.
8. **Wording, round 2**: the banner claimed "Facture supprimée de cette période" even when other, unrelated deletions could coexist on the same rectificatif — reverted to fully generic wording ("Cette période fait partie d'une correction de période liée à...") since the exact moved-invoice count can't be reliably attributed without a dedicated per-invoice link.
9. **Generalization to N-way groups**: Fabien asked how the design should handle a reporting linked to **more than one** other rectificatif at once (e.g. one period losing two different invoices to two different destination periods — not a 1:1 pair). This required a genuine data-model change:
   - `Reporting.linkedReportingId?: string` → `Reporting.linkedReportingIds?: string[]`
   - New per-invoice pointers `Invoice.movedToReportingId?: string` / `Invoice.movedFromReportingId?: string`, since with more than 2 reportings involved, a generic "origin === deleted" filter on a reporting's invoices is no longer enough to know *which* linked reporting each specific invoice moved to.
   - Component logic: `linkedGroup` (BFS traversal over `linkedReportingIds`, collecting all still-pending linked reportings, transitively), `transmitGroup` (the whole group sorted chronologically), `transmitGroupMoves` (per-invoice move records with exact origin/destination reporting, derived from the new pointers rather than a generic pair).
   - Banner and modal wording made count-aware for both the simple-pair case (unchanged wording) and the N>2 group case ("Cette période fait partie d'un groupe de N rectificatifs liés").
   - New mock scenario added to demonstrate it: EntitéG achats, "01 – 31 mai 2025" reporting loses two different invoices to two different destination periods, "01 – 30 juin 2025" and "01 – 31 juil. 2025".

### Documentation

The new use cases were added to the "Cartographie des tâches" Notion page as a new section (If/When/Then table format, matching the existing test-case checklist convention) with the exact test periods called out (EntitéG achats: Février/Mars 2025 for the simple pair, Mai/Juin/Juillet 2025 for the 3-way group) — and the corresponding "hors scope" bullet ("Correction de période : le résultat du double rectificatif, info à afficher / présenter ?") was removed since it's now covered.

### Deploy

Shipped as PR #357. The branch was 11 commits behind `main` at push time; merging surfaced a conflict on the two touched files caused by `main` having received the prior PR (#346) via a **squash-merge** — the squash commit doesn't share ancestry with the branch's own pre-squash commits, so git re-diffs against an older common ancestor and finds large (but not actually conflicting in substance) overlapping hunks. Verified by diffing `origin/main` against the branch's pre-new-work commit: the only real difference was the two-line `flowType` fix (present on the branch, not yet on `main`, because it was pushed after PR #346 had already been merged). Resolved by keeping the branch's version of both files (`git checkout --ours`) after explicit confirmation from Fabien, since the branch's content was verified to be a strict superset of `main`'s for those files. This is the second time this exact squash-merge-conflict pattern has occurred on this prototype branch (the first was against the older PR #311).

## Open items carried forward

- Whether the target-vision bundled-transmission design (built here as a prototype/maquette) should inform an actual product decision once cross-period correction needs to leave V1's SIM-side block — not yet decided, this was explicitly framed as exploration ("vision cible"), not a committed roadmap item.
- Whether a backend-side sequencing guarantee (never dispatch the "addition" file to Cegedim until the "removal" file is confirmed accepted) is technically feasible — flagged as a question for the backend/Cegedim integration team, not resolved in this session.
- The other open items from the 2026-08-21 progress note (manual "cancel this rectificatif" action, achats/ventes visual-consistency on in-progress status, terminology cleanup) were not addressed in this session.
