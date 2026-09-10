---
last_reviewed: 2026-08-26
---

# E-Reporting Rectificatif

> A corrective VAT e-reporting that replaces a previously-transmitted (or never-transmitted) reporting period once accepted by the tax administration.

## What it is

A rectificatif targets one specific [reporting period](Reporting_Period.md) and is created implicitly — never by an explicit "create rectificatif" action — whenever a client adds, modifies, or deletes an invoice or B2C transaction/payment on a period that was already transmitted. Each rectificatif links to its predecessor; the most recently **accepted** transmission is the sole source of truth for the tax administration for that period (the team deliberately avoids "initial" as a label, preferring "previous reporting," since each acceptance overwrites the prior state). A rectificatif that ends up empty, or that reverts to a state identical to the previous accepted version, should be deleted (manually in V1, automatically in the target vision once [Cegedim](../entities/Cegedim.md) ships a delete-project endpoint).

## Why it matters at Agicap

Core to Data Integration's e-invoicing/e-reporting compliance work (French VAT reform). Directly implemented by the `rectification-achats-v2` prototype in `agicap-prototypes`. Squad is deliberately scoping delivery by **source channel** first — AP/purchase invoices end-to-end, then Public API, then manual entries — rather than by feature depth, to avoid diluting focus across all three at once.

## Current status

- 🟢 In progress — the object model, one-row-per-period Historique behavior, read-only lock, and direct-to-rectificatif navigation agreed in the [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) are now built in the `rectification-achats-v2` prototype, for both AP/achats and Public API/ventes source channels. See [2026-08-21 implementation progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md) for the detailed breakdown.
- 🟢 As of 2026-08-26, a rectificatif's status model has an explicit intermediate step: `to-rectify` ("À transmettre") → `transmitted` ("Transmis") → `accepted` ("Accepté") — transmission and acceptance are no longer conflated. See [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md).
- 🟢 As of 2026-08-26, prototyped a target-vision answer to cross-period corrections: see [Period-Correction Bundling](Period-Correction_Bundling.md) — transmitting every rectificatif born from the same period correction as one grouped action, to avoid a DGFiP duplicate-declaration risk. Not yet a product commitment.
- 🟡 Still open: a manual "cancel this rectificatif" action (V1 = manual deletion, per the squad sync — not yet built), visual consistency between achats and ventes on whether the original's status changes while a rectificatif is open, and the prototype wording/tag cleanup action item from the squad sync.
- 🔴 Out of scope for now: cross-period date modifications remain blocked upstream in SIM for V1 (a deliberate, pragmatic choice — see [Reporting Period](Reporting_Period.md) and [Period-Correction Bundling](Period-Correction_Bundling.md) for the target-vision design), per-field value diffs (tag-only for MVP), Cegedim/PPF rejection surfacing in history.

## Related concepts

- [Reporting Period](Reporting_Period.md) — the unit a rectificatif always targets
- [Period-Correction Bundling](Period-Correction_Bundling.md) — target-vision mechanism for transmitting linked rectificatifs together when a correction spans periods
- [FRR Flow](FRR_Flow.md) — the file generated and sent to Cegedim when a rectificatif is transmitted
- [DGFIP / PPF](DGFIP_PPF.md) — the tax administration the rectificatif is ultimately destined for
- [Public API Invoice Ingestion](Public_API_Invoice_Ingestion.md) — a second source channel, planned for Step 2
- [B2C Manual Entries](B2C_Manual_Entries.md) — a third source channel, planned for Step 3

## Related entities

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — functional lead, delivery sequencing
- [Audric Podmilsak](../entities/Audric_Podmilsak.md) — technical feasibility, AP-first argument
- [Paul Sorrentino](../entities/Paul_Sorrentino.md) — UX consistency with initial reporting
- [Cegedim](../entities/Cegedim.md) — transmission intermediary

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-21 implementation progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md)
- [2026-08-26 synthesis](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Audric Podmilsak](../entities/Audric_Podmilsak.md)
- [Cegedim](../entities/Cegedim.md)
- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md)
- [Paul Sorrentino](../entities/Paul_Sorrentino.md)

**Concepts**

- [B2C Manual Entries](B2C_Manual_Entries.md)
- [DGFIP PPF](DGFIP_PPF.md)
- [FRR Flow](FRR_Flow.md)
- [Period-Correction Bundling](Period-Correction_Bundling.md)
- [Public API Invoice Ingestion](Public_API_Invoice_Ingestion.md)
- [Reporting Period](Reporting_Period.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-21 rectification-achats-v2-implementation-progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md)
- [2026-08-26 rectification-achats-v2-period-correction-bundling](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
