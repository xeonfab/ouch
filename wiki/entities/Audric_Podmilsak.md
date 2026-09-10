---
last_reviewed: 2026-08-20
---

# Audric Podmilsak

> Engineering perspective on e-reporting rectificatif — surfaces technical cost and edge cases.

## Identity

- **Role**: Engineering (backend — exact title unconfirmed)
- **Org / team**: Agicap — Data Integration / e-invoicing squad

## Relevance to me

Pushes back on scope from a build-cost angle: flags what's expensive (per-value diffs, cross-reporting history reconstruction), what [Cegedim](Cegedim.md) actually requires (rejection endpoints, FRR generation), and argues for scoping Step 1 to the AP/purchase channel end-to-end before generalizing to other sources.

## Key topics

- [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md) — technical feasibility and sequencing (AP-first strategy)
- [Cegedim](Cegedim.md) integration — transmission ID, FRR generation, rejection handling
- Diff/comparison cost tradeoffs (tag-only vs. per-field value diff)

## Interactions

- **2026-08-20** — squad sync on e-reporting rectificatif; argued for AP-channel-first sequencing and flagged the duplicate-invoice risk on cross-period moves → [synthesis](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

## Related

- Concepts: [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md), [FRR Flow](../concepts/FRR_Flow.md)
- Entities: [Cegedim](Cegedim.md)
- Syntheses: [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

## Sources

- `raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md`

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md)
- [FRR Flow](../concepts/FRR_Flow.md)
- [Public API Invoice Ingestion](../concepts/Public_API_Invoice_Ingestion.md)
- [Reporting Period](../concepts/Reporting_Period.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-21 rectification-achats-v2-implementation-progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
