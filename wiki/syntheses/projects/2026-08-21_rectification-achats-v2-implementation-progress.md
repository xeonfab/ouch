---
last_reviewed: 2026-08-21
---

# Rectification-achats-v2 — implementation progress (post squad sync)

> One-line TL;DR: the object model and UX agreed in the 2026-08-20 squad sync are now built in the `rectification-achats-v2` prototype — with three gaps still open.

| Field | Value |
|---|---|
| **Date** | 2026-08-21 |
| **Type** | project |
| **Participants** | Fabien Riou (product), Claude (prototype implementation) |
| **Source(s)** | `raw/articles/2026-08-21_rectification-achats-v2-implementation-update.md` |

---

## Context

Follow-up to the [2026-08-20 squad sync](../meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md), which agreed the rectification object model, UX flow, and Historique redesign for corrective e-reporting. This entry tracks how much of that agreement has actually been implemented in the `rectification-achats-v2` prototype (`agicap-prototypes` repo) versus what remains open.

## Key points

### Rectification object model — built

- Rectificatif creation (both AP/achats and Public API/ventes source channels) now clones the **entire** invoice list of the previously-transmitted reporting — the deleted invoice tagged, every other invoice tagged "unchanged" — rather than a single-invoice-only rectificatif. This matches the squad sync's point that annule/remplace sends full content, not a delta.
- Shared cloning logic extracted so achats and ventes don't duplicate the same pattern.

### Historique model — built, and it supersedes an earlier (2026-08-19) plan

- `transmit()` now removes the predecessor reporting from the list when transmitting a linked rectificatif, so there is exactly **one row per period** showing the latest accepted state — no second "Annulé" row.
- A lightweight "Rectifié" tag renders on any Historique row whose `sourceReportingId` link is set, satisfying the "trace back to what changed without duplicating rows" requirement.
- Historique list now sorts by period (ascending), not send date.
- Note for anyone cross-referencing older notes: a *different* 2026-08-19 workshop (documented elsewhere, in the Agicap PrD squad wiki, not this one) had proposed keeping every transmission with a distinct "Annulé" status on superseded ones. The 2026-08-20 squad sync explicitly reversed that in favor of the one-row-per-period model described here — no "Annulé" status exists in this prototype.

### UX flow — built

- Creating/updating a rectificatif from an already-transmitted reporting now navigates the user directly to the rectificatif's detail view, not back to a list.
- Read-only lock implemented via a cross-reporting lookup (find any `to-rectify` reporting whose `sourceReportingId` points back to the one being viewed) — deliberately independent of whether the original's own status field changed, so it works the same for achats and ventes even though those two channels aren't yet visually consistent with each other (see Open questions).
- A caution banner ("Rectificatif en cours pour cette période... en lecture seule") with a link to the open rectificatif appears on a locked reporting; its delete actions are hidden/disabled instead.

### Rejected corrections — built

- Mock reportings previously shown in Historique with status "rejected" were moved into "À transmettre" with status `to-rectify`, per the rule that rejected corrections never enter history.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien Riou / Claude | Build a manual "cancel this rectificatif" action (V1 = manual, not automatic) | — | open |
| Fabien Riou / Claude | Align achats and ventes on whether the original's status visually changes while a rectificatif is open | — | open |
| Fabien Riou | Clean up prototype wording/tags ("modifié", "supprimé", "en cours") — carried over from the 2026-08-20 squad sync action item, still not actioned | — | open |

## Open questions

- Should achats also flip a visible status (like ventes' "rectifying") while a correction is drafted, or should ventes instead be changed to match achats' silence? The read-only lock works either way — this is purely a visual-consistency question, not a functional gap.
- What exact replacement wording does Fabien want for "modifié"/"supprimé"/"en cours" tags, and for "reporting initial" → "reporting précédent"? The squad sync flagged the need but didn't specify replacements.

## Related wiki pages

- Entities: [Ludovic Lelievre](../../entities/Ludovic_Lelievre.md), [Audric Podmilsak](../../entities/Audric_Podmilsak.md), [Paul Sorrentino](../../entities/Paul_Sorrentino.md)
- Concepts: [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md), [Public API Invoice Ingestion](../../concepts/Public_API_Invoice_Ingestion.md)

## Sources

- [raw/articles/2026-08-21_rectification-achats-v2-implementation-update.md](../../../raw/articles/2026-08-21_rectification-achats-v2-implementation-update.md)
- Builds on: [2026-08-20 squad sync](../meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [E-Reporting Rectificatif](../../concepts/E-Reporting_Rectificatif.md)
- [Public API Invoice Ingestion](../../concepts/Public_API_Invoice_Ingestion.md)

**Syntheses**

- [2026-08-26 rectification-achats-v2-period-correction-bundling](2026-08-26_rectification-achats-v2-period-correction-bundling.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC E-Reporting Rectificatif](../../mocs/MOC_E-Reporting_Rectificatif.md)

<!-- BACKLINKS:END -->
