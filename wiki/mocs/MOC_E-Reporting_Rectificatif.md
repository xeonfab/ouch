---
last_reviewed: 2026-08-26
---

# 🗺️ MOC: E-Reporting Rectificatif

> Corrective VAT e-reporting on purchase invoices (`rectification-achats-v2` prototype): the object model, the source-channel rollout sequencing, and the target-vision answer to the cross-period duplicate-declaration risk.

---

## 🧠 Core concepts

- [E-Reporting Rectificatif](../concepts/E-Reporting_Rectificatif.md) — the corrective reporting object itself: creation, status model, read-only lock
- [Reporting Period](../concepts/Reporting_Period.md) — the SIREN + date-range unit a rectificatif always targets, and why cross-period moves are blocked in V1
- [Period-Correction Bundling](../concepts/Period-Correction_Bundling.md) — target-vision mechanism for transmitting linked rectificatifs together, avoiding a DGFiP duplicate-declaration
- [FRR Flow](../concepts/FRR_Flow.md) — the e-reporting file generated and sent to Cegedim per period
- [DGFIP / PPF](../concepts/DGFIP_PPF.md) — the tax administration and portal e-reporting is ultimately destined for
- [Public API Invoice Ingestion](../concepts/Public_API_Invoice_Ingestion.md) — second source channel, planned for Step 2
- [B2C Manual Entries](../concepts/B2C_Manual_Entries.md) — third source channel, planned for Step 3

## 👥 Key entities

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — functional lead, delivery sequencing
- [Audric Podmilsak](../entities/Audric_Podmilsak.md) — engineering perspective, AP-first strategy
- [Paul Sorrentino](../entities/Paul_Sorrentino.md) — UX consistency with initial reporting
- [Cegedim](../entities/Cegedim.md) — transmission intermediary between Agicap and DGFIP/PPF

## 📚 Syntheses & strategy

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) — original object model, UX flow, phased delivery plan; the decision to block cross-period corrections in V1
- [2026-08-21 implementation progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md) — object model, Historique redesign, and read-only lock built in prototype
- [2026-08-26 period-correction bundling](../syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md) — status model refinement (Transmis vs Accepté), UX fix batch, and the bundled-transmission target-vision design/prototype

## ❓ Open questions

- Should the bundled-transmission design (period-correction bundling) become a real product commitment, and when does cross-period correction actually need to leave V1's SIM-side block?
- Does Cegedim/PPF guarantee or require any processing-order sequencing between two files sent close together? Unresolved — needs the backend/Cegedim integration team.
- Manual "cancel this rectificatif" action, achats/ventes visual-consistency on in-progress status, and prototype terminology cleanup — all flagged since 2026-08-20/21, still open as of 2026-08-26.

## 📥 Raw sources worth re-reading

- [raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md](../../raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md) — the fullest, most recent implementation detail

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../index.md)

<!-- BACKLINKS:END -->
