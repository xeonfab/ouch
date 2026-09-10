---
last_reviewed: 2026-08-26
---

# DGFIP / PPF

> The French tax administration (DGFIP) and its public invoicing portal (PPF), the ultimate destination of e-reporting flows.

## What it is

DGFIP (Direction Générale des Finances Publiques) is the French tax authority; PPF (Portail Public de Facturation) is its public platform in the e-invoicing reform chain. Agicap does not talk to DGFIP/PPF directly — it transmits via [Cegedim](../entities/Cegedim.md), which forwards the [FRR flow](FRR_Flow.md). PPF performs no additional checks beyond the official schema Agicap already validates against upstream; a real PPF-side rejection is considered a rare edge case ("something broke on PPF's side").

## Why it matters at Agicap

Defines the acceptance semantics the whole rectificatif model hinges on: a reporting period is only considered "final" once DGFIP/PPF (via Cegedim) has accepted it — that's the moment the "Historique" list should replace the previous period entry (see [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)).

## Current status

- 🟢 Live — initial reporting already integrates with this pipeline.
- 🟡 Planned — rectificatif transmission will reuse the same acceptance semantics.
- 🟡 Known risk (2026-08-26) — a cross-period invoice correction sent as two independent, out-of-order transmissions can make DGFIP see the same invoice declared in two periods at once. Currently sidestepped by blocking cross-period corrections in V1; see [Period-Correction Bundling](Period-Correction_Bundling.md) for the target-vision mechanism explored to solve it properly.

## Related concepts

- [FRR Flow](FRR_Flow.md) — the file transmitted through Cegedim to reach DGFIP/PPF
- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — depends on DGFIP/PPF acceptance to finalize a period
- [Period-Correction Bundling](Period-Correction_Bundling.md) — mechanism designed to avoid declaring the same invoice twice to DGFIP

## Related entities

- [Cegedim](../entities/Cegedim.md) — intermediary between Agicap and DGFIP/PPF
- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — clarified that real rejections are handled by Cegedim upstream, not PPF

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Cegedim](../entities/Cegedim.md)

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
