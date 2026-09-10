---
last_reviewed: 2026-08-26
---

# Period-Correction Bundling

> Transmitting every rectificatif born from the same period correction as a single user-facing action, to prevent the same invoice from being declared to the DGFiP in two periods at once.

## What it is

A "correction de période" — an invoice's issue date corrected such that it moves from one declared VAT period to another — always produces more than one [rectificatif](E-Reporting_Rectificatif.md): an annule/remplace on the losing period, plus a new/updated reporting on each receiving period. Left as independent transmissions, these can be sent out of order or partially, leaving the same invoice declared present in two periods simultaneously — a duplicate-declaration risk with the DGFiP.

Period-correction bundling is the target-vision answer prototyped in `rectification-achats-v2`: the linked rectificatifs are treated as **one transmission group**. Clicking "Transmettre" on any reporting in the group opens a shared recap listing every moved invoice with its exact origin and destination period, and confirming transmits the whole group together. The object model generalizes from a 1:1 pair to an N-way group, since a single period can lose different invoices to different destination periods at once:

- `Reporting.linkedReportingIds?: string[]` — every directly-linked "sibling" reporting (not `sourceReportingId`, which links a rectificatif to the reporting it supersedes)
- `Invoice.movedToReportingId?: string` / `movedFromReportingId?: string` — per-invoice pointer to the exact counterpart reporting, needed once more than two reportings are involved and a generic "deleted here" filter can no longer say *which* destination a given invoice moved to
- A BFS traversal over `linkedReportingIds` (component logic: `linkedGroup`) collects the full transitively-connected set of still-pending linked reportings

A recommended (not yet committed) backend-side safety net complements the UI guarantee: never actually dispatch the "addition" file to Cegedim until the "removal" file is confirmed accepted — protecting against cases the UI alone can't cover (a lost connection mid-transmission, a future automated batch path).

## Why it matters at Agicap

Directly addresses a gap the squad had already worked around, not solved: the [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) chose to block cross-period corrections entirely upstream in SIM for V1, explicitly to sidestep this exact duplicate-declaration risk — a pragmatic "move fast" call, not a permanent architectural answer (see [Reporting Period](Reporting_Period.md)). This concept is the explored **target-vision** mechanism for when that block eventually needs to lift, e.g. once cross-period correction is supported via Public API/V2 sources — the "Cartographie des tâches" doc already described a 2-rectificatifs mechanic as active there, just not previously surfaced in UI.

## Current status

- 🟢 Prototyped — built and iterated in `rectification-achats-v2` (info banner + shared "Aperçu avant transmission" recap modal + N-way group transmission), shipped as PR #357. See [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md) for the full design iteration history.
- 🟡 Not a product commitment — explicitly framed as "vision cible" exploration, not yet decided whether it becomes the real V2/Public-API mechanism.
- 🟡 Open: whether Cegedim/PPF technically supports or requires any processing-order guarantee between two files sent seconds apart — unresolved, needs the backend/Cegedim integration team.

## Related concepts

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — the object this mechanism groups for transmission
- [Reporting Period](Reporting_Period.md) — the unit that gets blocked from cross-period movement in V1, which this concept is the target-vision answer to
- [DGFIP / PPF](DGFIP_PPF.md) — the tax administration the duplicate-declaration risk is against
- [FRR Flow](FRR_Flow.md) — the file(s) that would need coordinated dispatch

## Sources

- [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)
- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) — origin of the V1 blocking decision this concept responds to

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [DGFIP PPF](DGFIP_PPF.md)
- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)
- [Reporting Period](Reporting_Period.md)

**Syntheses**

- [2026-08-26 rectification-achats-v2-period-correction-bundling](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
