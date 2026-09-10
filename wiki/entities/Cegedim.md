---
last_reviewed: 2026-08-20
---

# Cegedim

> The PDP / intermediary partner platform Agicap transmits e-reporting flows through on the way to the French tax administration.

## Identity

- **Role**: External partner platform (PDP — Plateforme de Dématérialisation Partenaire)
- **Org / team**: External vendor, not Agicap

## Relevance to me

Sits between Agicap and [DGFIP/PPF](../concepts/DGFIP_PPF.md) in the e-reporting pipeline: Agicap generates a complete FRR file and sends it to Cegedim, which returns a transmission ID; that ID is later used to check acceptance/rejection status. A future "delete rectification project" endpoint from Cegedim is a prerequisite for fully-automatic cleanup of empty/no-op rectificatifs (see [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md)).

⚠️ Name was auto-transcribed inconsistently in the source meeting ("CGDIM," "Jedim," "Cim") — confirmed spelling is **Cegedim**.

## Key topics

- [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md) — transmission ID, future delete-project endpoint
- [FRR Flow](../concepts/FRR_Flow.md) — the file format/flow sent to Cegedim
- Rejections: Cegedim-side rejections are considered rare/edge since Agicap validates against the official schema before sending

## Interactions

- **2026-08-20** — discussed as the transmission intermediary and as the source of a not-yet-available delete-project endpoint → [synthesis](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

## Related

- Concepts: [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md), [FRR Flow](../concepts/FRR_Flow.md), [DGFIP / PPF](../concepts/DGFIP_PPF.md)

## Sources

- `raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md`

---

<!-- BACKLINKS:START -->
## Referenced by

**Entities**

- [Audric Podmilsak](Audric_Podmilsak.md)

**Concepts**

- [DGFIP PPF](../concepts/DGFIP_PPF.md)
- [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md)
- [FRR Flow](../concepts/FRR_Flow.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
