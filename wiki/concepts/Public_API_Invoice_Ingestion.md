---
last_reviewed: 2026-08-21
---

# Public API Invoice Ingestion

> The channel through which AP (Accounts Payable) clients push invoice creates/updates/deletes directly to Agicap, bypassing manual entry.

## What it is

AP-side clients have a direct link into Agicap (not through Agicap's own public API from their side): they send a POST for invoice creation, a PUT for modification, or a DELETE, and Agicap currently accepts all of it. The one exception: anything out-of-period today is rejected outright ("hors période," rendered in red) — a stance the squad acknowledges is not sustainable long-term, since it doesn't distinguish a genuine mistake needing correction from noise. AP has also signaled it wants to "de-responsibilize" itself from this reconciliation — long-term, Agicap expects to invert the dependency (Agicap pulls, rather than AP pushes).

## Why it matters at Agicap

This is the **second** source channel targeted for [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) support (Step 2, after the AP/purchase-channel core in Step 1). Because it's already a create/update/delete API, the squad expects it to be technically easier to slot into the rectification model than manual sources.

## Current status

- 🟢 Live — accepts create/update/delete for in-period invoices.
- 🟡 Planned — routing out-of-period create/update/delete into automatic rectificatif generation (Step 2).
- 🔴 Not yet supported — deleting a B2B invoice manually when it originated from this API is an open question, unresolved in this session.
- 🟡 Prototype exploration (not a validated backend decision): `rectification-achats-v2` now demonstrates one possible answer to the manual-deletion question above — deleting a Public-API-sourced invoice from an already-transmitted ventes reporting creates/updates a rectificatif cloning the full invoice list, and locks the original as read-only until that rectificatif is transmitted. See [2026-08-21 implementation progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md).

## Related concepts

- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md) — target mechanism this channel will plug into
- [B2C Manual Entries](B2C_Manual_Entries.md) — the third channel, manual rather than API-driven

## Related entities

- [Ludovic Lelievre](../entities/Ludovic_Lelievre.md) — flagged the need to reject out-of-period invoices consistently across channels
- [Audric Podmilsak](../entities/Audric_Podmilsak.md) — clarified current accept-all / reject-out-of-period behavior and the long-term dependency inversion

## Sources

- [2026-08-20 squad sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-21 implementation progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [B2C Manual Entries](B2C_Manual_Entries.md)
- [E-Reporting Rectificatif](E-Reporting_Rectificatif.md)

**Syntheses**

- [2026-08-20 e-reporting-rectificatif-squad-sync](../syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)
- [2026-08-21 rectification-achats-v2-implementation-progress](../syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
