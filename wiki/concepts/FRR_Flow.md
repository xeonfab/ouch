---
last_reviewed: 2026-08-20
---

# FRR Flow

> The complete e-reporting file Agicap generates and transmits to Cegedim for a given reporting period.

## What it is

FRR ("Fichier Reporting Rectificatif" per context — exact expansion unconfirmed in source) is the file format/flow Agicap builds from a period's invoices/transactions and sends to [Cegedim](../entities/Cegedim.md). Cegedim returns a transmission ID, which Agicap later uses to poll acceptance/rejection status before [DGFIP/PPF](DGFIP_PPF.md). Today Agicap constructs the FRR from individual B2C invoices/transactions/payments; a discussed (deprioritized) alternative is letting clients push a complete FRR flow directly instead.

## Why it matters at Agicap

Every transmit action (initial or rectificatif) ultimately produces one FRR generation + send. The mechanics are the same for both — the pipeline is generate → send to Cegedim → get transmission ID → poll status.

## Current status

- 🟢 Live — FRR generation/transmission mechanics already exist for initial reporting.
- 🟡 Planned — reuse of the same mechanics for rectificatif transmission (see [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)).
- 🔴 Deprioritized — direct client-side FRR push (skipping Agicap's own FRR assembly) discussed as a "nice to have," not scheduled.

## Related concepts

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — triggers FRR generation on transmit
- [Reporting Period](Reporting_Period.md) — the scope of one FRR file
- [DGFIP / PPF](DGFIP_PPF.md) — final destination after Cegedim

## Related entities

- [Cegedim](../entities/Cegedim.md) — receives the FRR, returns the transmission ID
- [Audric Podmilsak](../entities/Audric_Podmilsak.md) — described the generate/send/poll mechanics

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Audric Podmilsak](../entities/Audric_Podmilsak.md)
- [Cegedim](../entities/Cegedim.md)

**Concepts**

- [DGFIP PPF](DGFIP_PPF.md)
- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)
- [Period-Correction Bundling](Period-Correction_Bundling.md)
- [Reporting Period](Reporting_Period.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
