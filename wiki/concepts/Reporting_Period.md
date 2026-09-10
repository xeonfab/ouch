---
last_reviewed: 2026-08-26
---

# Reporting Period

> The unit an e-reporting (initial or rectificatif) always targets — keyed by SIREN + date range.

## What it is

A reporting period is identified by the seller's SIREN and a date range (e.g. "1–15 August"). At most one reporting object exists per period at any time in history: when a new transmission for that period is accepted, it takes the place of the previous one. This is why an invoice's date is treated as a near-immutable key — changing it moves the invoice to a different period and cascades into cross-period rectification (see [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)), which the squad has chosen to block rather than support in V1 — a deliberate, pragmatic "move fast" call specifically to sidestep the DGFiP duplicate-declaration risk a cross-period move creates (see [Period-Correction Bundling](Period-Correction_Bundling.md) for the target-vision mechanism explored for when this block eventually needs to lift), not a sign the risk is unsolvable.

## Why it matters at Agicap

Determines how the "Historique" list is structured: one row per period (not per transmission event), sorted by period rather than by send date, so accountants can always find "what did we declare for this period" regardless of when a correction was sent.

## Current status

- 🟡 Planned — same-period add/modify/delete is in scope for Step 1 of the rectificatif rollout; cross-period date changes are explicitly blocked in V1, not supported.
- 🟢 2026-08-26 — the target-vision mechanism for eventually supporting cross-period moves (bundled transmission of every linked rectificatif) was designed and prototyped; not yet a product commitment. See [Period-Correction Bundling](Period-Correction_Bundling.md).

## Related concepts

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — the mechanism that operates on a period
- [Period-Correction Bundling](Period-Correction_Bundling.md) — target-vision answer to the risk that blocks cross-period moves in V1
- [FRR Flow](FRR_Flow.md) — the file transmitted per period

## Related entities

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — pushed the "previous reporting" terminology over "initial"
- [Audric Podmilsak](../entities/Audric_Podmilsak.md) — identified SIREN + date as the period key

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md)

**Concepts**

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)
- [FRR Flow](FRR_Flow.md)
- [Period-Correction Bundling](Period-Correction_Bundling.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-26 rectification-achats-v2-period-correction-bundling](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
