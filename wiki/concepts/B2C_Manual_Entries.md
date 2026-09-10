---
last_reviewed: 2026-08-20
---

# B2C Manual Entries

> Manually-entered B2C transactions and payments — a third, non-API source channel for e-reporting.

## What it is

Unlike AP invoices (pushed via [Public API](Public_API_Invoice_Ingestion.md)), B2C transactions and payments can be entered manually by the client directly in Agicap. Once a reporting for a period is transmitted, manually adding, modifying, or deleting one of these entries should auto-generate/update a [rectificatif](E-Reporting_Rectificatif.md) for that period, the same way AP-sourced actions do. There is no delete endpoint from Cegedim today, so a manually-deleted B2C entry (or a manually-deleted sales invoice, for that matter) simply never gets sent — this already happens today for the *initial* (non-corrective) reporting.

## Why it matters at Agicap

Third and last source channel targeted for [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) support (Step 3, after AP and Public API). Also the channel where a "create transaction" button incorrectly remains available even after a sales reporting has been transmitted — a gap the squad wants closed as part of the Step 0 safety net.

## Current status

- 🟡 Planned — routing manual B2C add/modify/delete into rectificatif generation (Step 3).
- 🔴 Not supported — sales-side out-of-period rejection doesn't exist yet (unlike the AP/purchase channel); this is the Step 0 prerequisite.

## Related concepts

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — target mechanism this channel will plug into
- [Public API Invoice Ingestion](Public_API_Invoice_Ingestion.md) — the API-driven counterpart channel

## Related entities

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — flagged the missing out-of-period guard on this channel as Step 0

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)
- [Public API Invoice Ingestion](Public_API_Invoice_Ingestion.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
