---
last_reviewed: 2026-08-20
---

# E-reporting rectificatif — squad sync

> Squad works through the lifecycle, UI states, and phased delivery plan for corrective ("rectificatif") e-reporting on purchase invoices (AP channel).

| Field | Value |
|---|---|
| **Date** | 2026-08-20 |
| **Type** | meeting |
| **Participants** | [Ludovic Lelievre](../../entities/Ludovic_Lelievre.md), [Audric Podmilsak](../../entities/Audric_Podmilsak.md), [Paul Sorrentino](../../entities/Paul_Sorrentino.md), Fabien Riou (you) |
| **Source(s)** | `raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md` |

---

## Context

Follow-up design session on how Agicap should let clients correct a VAT e-reporting that was already transmitted to the tax administration (via [Cegedim](../../entities/Cegedim.md) as PDP/intermediary, then [DGFIP/PPF](../../concepts/DGFIP_PPF.md)). Fabien Riou walks the squad through a prototype of the "add/modify/delete → rectificatif" flow for purchase invoices; the group settles the object model, the history/list UI, and a phased delivery plan. Directly feeds the `rectification-achats-v2` prototype in this repo.

## Key points

### Rectification object model
- A [rectificatif](../../concepts/E-Reporting_Rectificatif.md) always targets a specific [reporting period](../../concepts/Reporting_Period.md) (key = SIREN + period dates). Two entry cases: (a) correcting a period that was already transmitted/accepted, (b) filling a period that was never transmitted at all.
- Each rectificatif links to its predecessor (bidirectional link: rectificatif → previous, previous → rectificatif). The **last transmitted** version is the source of truth for the tax admin — the team deliberately avoids the word "initial" in favor of "previous reporting," since each transmission overwrites the prior one.
- A rectificatif is, by construction, never a no-op: it only exists because *some* action (add/modify/delete) happened relative to the previous version.

### Auto-deletion rules for a rectificatif project
- If the draft rectificatif ends up empty, or reverts to a state identical to the previously-transmitted period, it should be deleted automatically.
- **V1**: manual deletion by the user. **Target vision**: fully automatic, gated on Cegedim shipping a "delete rectification project" endpoint.

### UX flow (agreed)
- Users never explicitly "open a rectificatif." From an already-transmitted reporting, adding/editing/deleting an invoice (via ERP/AP flow) or a manual B2C transaction/payment auto-generates or updates the rectificatif project for that period.
- If a rectification project is already in progress for a period, further actions land in that same open project; the already-transmitted reporting becomes read-only with a "project in progress" banner linking to it.
- After creating a rectificatif, the user should land directly on the rectificatif view — not back on a list — so they can see the diff (deleted line + all carried-over lines) immediately.

### History / list view
- One row per period in "Historique," always showing the **latest accepted** state — not one row per transmission event. Rejected corrections stay in "à transmettre" (to-transmit) tagged "à rectifier," and never enter history.
- Transmitting a rectificatif doesn't immediately flip history to the new version: it only replaces the previous period entry once accepted by the tax admin (mirrors how initial reportings already behave). Until then it sits in "to transmit" as "in progress."
- A lightweight "rectificatif" tag/link on the history row (rather than a second status) lets a user trace back to what changed, without duplicating rows per period.
- Sort by period (ascending), not by send date — accountants care about "what did we declare for this period," not "what did we just send."

### Diff / change display
- MVP: a simple "modified" tag per invoice line, not a value-level diff (e.g. "2000 struck through, 100 next to it") — the latter is deferred to a later user story since it's costlier to build well.

### Deliberately deferred edge cases
- **Cross-period date changes**: editing an invoice's date so it moves to a different reporting period cascades into two auto-generated rectificatifs (delete in period A, add in period B). Flagged as a real risk — if only one of the two gets manually transmitted, the invoice could be duplicated at the tax admin. No solution agreed; parked as a future/separate topic. V1 rule: **block** cross-period date modifications for AP-sourced invoices.
- Potentially long/branching chains of linked reportings when multiple invoices move between periods — acknowledged as rare, not solved.
- Cegedim-side / PPF-side rejections are considered acceptable to hide from history for now — official schemas are validated upstream, so real rejections are expected to be edge cases.

### Phased delivery plan
- **Step 0** (safety net, small): sales-side ("vente") e-reporting doesn't yet reject out-of-period invoices the way the purchase/AP channel does — add the same guard (reject with an error) before building rectification logic, so sales reporting doesn't get polluted by unhandled corrective imports in the meantime. Also block the "create B2C transaction" action once a sales reporting is already transmitted.
- **Step 1** (the big chunk, front + back): full rectification core for **AP/purchase-channel** flows only — same-period add/modify/delete, up to manual transmission. Includes sub-item 1.2: block cross-period ("interpériode") date modifications.
- **Step 2**: apply the same logic to **Public API** sources.
- **Step 3**: apply to **manual sources** (B2C transactions/payments, manual sales-invoice deletion).
- Comparison/diff logic (tagging modified/added/deleted) can be split into its own user story — MVP ships with modify-only tagging, degraded mode, no value-level diff.

### Other roadmap items (mentioned, not detailed)
- Initial (non-corrective) payment e-reporting — slightly higher near-term priority since it's needed sooner.
- Letting clients push a complete FRR flow directly (instead of individual B2C invoices/transactions that Agicap assembles into FRR) — a "nice to have," explicitly deprioritized.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Squad | Deliver Step 0 (block out-of-period sales imports) before starting rectification work | — | open |
| Squad | Scope Step 1 to AP-channel only, blocking cross-period date edits | — | open |
| Ludovic Lelievre | Continue plan breakdown in Notion, revisit remaining items (initial payment reporting, FRR push) next session | 2026-08-21 (next day) | open |
| Fabien Riou | Clean up prototype wording/tags (e.g. "modifié," "supprimé," "en cours") based on session feedback | — | open |

## Open questions

- What happens if a client transmits only one of two auto-generated rectificatifs from a cross-period move (risk of duplicate invoice at the tax admin)? No agreed answer — parked.
- Exact spelling/identity confirmed: the partner platform is **Cegedim**, not "CGDIM"/"Jedim" as auto-transcribed.
- How should the history "in progress" tag be surfaced without adding a confusing second status column? Landed on a tag/link rather than a second status, but exact placement (period column vs. status column) still to be finalized.

## Related wiki pages

- Entities: [Ludovic Lelievre](../../entities/Ludovic_Lelievre.md), [Audric Podmilsak](../../entities/Audric_Podmilsak.md), [Paul Sorrentino](../../entities/Paul_Sorrentino.md), [Cegedim](../../entities/Cegedim.md)
- Concepts: [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md), [Reporting Period](../../concepts/Reporting_Period.md), [FRR Flow](../../concepts/FRR_Flow.md), [DGFIP / PPF](../../concepts/DGFIP_PPF.md), [Public API Invoice Ingestion](../../concepts/Public_API_Invoice_Ingestion.md), [B2C Manual Entries](../../concepts/B2C_Manual_Entries.md)

## Sources

- [raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md](../../../raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Audric Podmilsak](../../entities/Audric_Podmilsak.md)
- [Cegedim](../../entities/Cegedim.md)
- [Ludovic Lelievre](../../entities/Ludovic_Lelievre.md)
- [Paul Sorrentino](../../entities/Paul_Sorrentino.md)

**Concepts**

- [B2C Manual Entries](../../concepts/B2C_Manual_Entries.md)
- [DGFIP PPF](../../concepts/DGFIP_PPF.md)
- [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md)
- [FRR Flow](../../concepts/FRR_Flow.md)
- [Period-Correction Bundling](../../concepts/Period-Correction_Bundling.md)
- [Public API Invoice Ingestion](../../concepts/Public_API_Invoice_Ingestion.md)
- [Reporting Period](../../concepts/Reporting_Period.md)

**Syntheses**

- [2026-08-21 rectification-achats-v2-implementation-progress](../projects/2026-08-21_rectification-achats-v2-implementation-progress.md)
- [2026-08-26 rectification-achats-v2-period-correction-bundling](../projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
