---
last_reviewed: 2026-08-26
---

# Rectification-achats-v2 — period-correction bundling and UX fixes

> One-line TL;DR: prototyped and shipped the target-vision solution to the DGFiP duplicate-declaration risk on cross-period corrections — bundled transmission of linked rectificatifs, generalized from a 1:1 pair to an N-way group — plus a batch of status-model and UX fixes from the 24/08 workshop.

| Field | Value |
|---|---|
| **Date** | 2026-08-26 |
| **Type** | project |
| **Participants** | Fabien Riou (product), Claude (prototype implementation) |
| **Source(s)** | `raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md` |

---

## Context

Continues the [2026-08-21 implementation progress](2026-08-21_rectification-achats-v2-implementation-progress.md), itself built on the [2026-08-20 squad sync](../meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md). Two batches of work in one continuous session: a set of targeted UX fixes from the 24/08 workshop, then a substantial new mechanism — bundled transmission for period corrections — designed and prototyped end-to-end.

## Key points

### Status model: Transmis vs Accepté — built

`transmit()` now sets an intermediate `transmitted` status instead of jumping straight to `accepted`, so the prototype no longer conflates "sent to the DGFiP" with "accepted by the DGFiP". `to-rectify` was also renamed "À rectifier" → "À transmettre" throughout, per the 24/08 workshop.

### Deletion/restoration lifecycle — built

- A rectificatif auto-deletes when every line reverts to "Inchangé", redirecting the user back to the **original** reporting it was correcting (not to Historique) — fixed after a wrong-redirect bug was caught in manual testing.
- Invoice deletion is now undoable ("Annuler la suppression" on the drawer).
- Bulk-selection exclusions (locked pré-comptabilité lines, already-deleted lines) now work correctly for achats too, not just ventes.

### List/table & dialog polish — built

Pagination on "À transmettre" and Historique; Historique's Statut column restored; transmit confirmation dialog simplified (single banner + horizontal description-list) with its confirm button changed from red to blue, since red read as alarming for a routine, expected action.

### Period-correction bundling — the substantial new mechanism, built and shipped

**The problem**: correcting an invoice's issue date across a period boundary always produces two rectificatifs (annule/remplace on the old period, new/updated reporting on the new one). Transmitted independently, out of order, the same invoice can be declared present in two periods at once — a DGFiP duplicate-declaration risk. The squad's [2026-08-20 sync](../meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) had already chosen to block cross-period corrections entirely upstream for V1 specifically to sidestep this, but flagged it as a pragmatic "move fast" call, not a permanent answer. This session designed the **target-vision** solution for when that block eventually needs to lift.

**Recommendation**: treat the linked rectificatifs as one user-facing transmission action — a single "Transmettre" bundles all linked files in the correct backend order, with a backend-side safety net (never dispatch the "addition" file until the "removal" file is confirmed accepted) as a second line of defense.

**What got built**, after several rounds of direct feedback:
- An info banner on every reporting that's part of a period-correction link, with a button opening a shared "Aperçu avant transmission" recap.
- The recap modal lists the actually-moved invoice(s) — each shown once (number, supplier, amount), with its exact origin and destination period — rather than duplicating the invoice under a "removed" and an "added" block, which read as a bug the first time it shipped.
- **Generalized from a 1:1 pair to an N-way transmission group**: `Reporting.linkedReportingId` (single string) became `linkedReportingIds` (array), plus new per-invoice pointers `movedToReportingId`/`movedFromReportingId` — needed because with more than 2 linked reportings, a generic "which invoices are deleted here" filter can no longer tell which *specific* destination each invoice moved to. A BFS traversal (`linkedGroup`) collects the full set of still-pending linked reportings transitively.
- Wording iterated multiple times: fixed a grammatically ambiguous banner, made invoice counts accurate (or fully generic when accuracy couldn't be guaranteed — a rectificatif can have unrelated deletions coexisting with period-correction moves), and enforced the Flipper DS's one-button-per-banner convention (an earlier two-button layout visually broke).
- New mock scenario demonstrating the N-way case: EntitéG achats, May 2025 loses two different invoices to two different destination periods (June 2025, July 2025).

Documented as a new test-case section in the "Cartographie des tâches" Notion page (If/When/Then format, exact test periods called out), with the corresponding "hors scope" item removed since it's now covered.

### Deploy

Two PRs: **#346** (the UX-fix batch, including a `flowType` bug fix flagged by the repo's security bot) and **#357** (period-correction bundling). Both surfaced the same recurring git issue on this branch: a prior PR gets squash-merged into `main`, and the next merge-back conflicts because the squash commit doesn't share ancestry with the branch's own pre-squash commits — verified safe both times by diffing `origin/main` against the branch's pre-new-work state and confirming the branch's content was a strict superset, then resolving with `git checkout --ours` after explicit confirmation.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien Riou | Decide whether the target-vision bundled-transmission design should inform a real product commitment once cross-period correction needs to leave V1's SIM-side block | — | open (explicitly framed as exploration, not a roadmap item) |
| Backend / Cegedim integration team | Confirm whether a backend-side sequencing guarantee (never send the "addition" file before the "removal" file is confirmed accepted) is technically feasible | — | open |
| Fabien Riou / Claude | Manual "cancel this rectificatif" action, achats/ventes visual-consistency, terminology cleanup — carried over from 2026-08-21, still not actioned | — | open |

## Open questions

- Does Cegedim/PPF guarantee any processing order between two files sent seconds apart, or is an explicit accept-then-send sequencing required? Unresolved, flagged for the backend team.
- Should the bundled-transmission UX (built here) become the actual V2/Public-API mechanism once cross-period correction is unblocked, or is a different mechanism preferable once real backend constraints are known?

## Related wiki pages

- Concepts: [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md), [Reporting Period](../../concepts/Reporting_Period.md), [Period-Correction Bundling](../../concepts/Period-Correction_Bundling.md), [DGFIP / PPF](../../concepts/DGFIP_PPF.md)
- Builds on: [2026-08-21 implementation progress](2026-08-21_rectification-achats-v2-implementation-progress.md), [2026-08-20 squad sync](../meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

## Sources

- [raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md](../../../raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [DGFIP PPF](../../concepts/DGFIP_PPF.md)
- [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md)
- [Period-Correction Bundling](../../concepts/Period-Correction_Bundling.md)
- [Reporting Period](../../concepts/Reporting_Period.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
