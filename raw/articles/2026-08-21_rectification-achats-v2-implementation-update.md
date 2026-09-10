# Rectification-achats-v2 — implementation update (post squad sync 2026-08-20)

Author: Claude (acting as prototype engineer for Fabien Riou), summarizing implementation work carried out in the `agicap-prototypes` repo, prototype `rectification-achats-v2`, directly following the decisions from the 2026-08-20 squad sync.

## Changes implemented

### 1. Rectificatif creation clones the full invoice list (achats and ventes)

Both `createOrUpdateRectificatifForHistoryDeletion` (achats) and `requestVentesInvoiceDeletionFromHistory` (ventes) now build a new rectificatif by cloning every invoice from the previously-transmitted reporting: the deleted invoice is tagged "deleted", every other invoice is tagged "unchanged". Previously the ventes path only included the single deleted invoice, which was flagged as fiscally incorrect (annule/remplace sends the full content, not the delta). Shared the invoice-cloning logic between the two flows via two private helpers (`cloneInvoicesWithOneDeleted`, `markInvoiceDeleted`) to avoid duplicating the pattern.

### 2. Historique model: one row per period, no separate "Annulé" status

`ReportingService.transmit(id)` now checks whether the reporting being transmitted has a `sourceReportingId` (i.e. it's a rectificatif). If so, its predecessor is removed from the list entirely, and the rectificatif becomes the sole surviving row for that period — carrying `sourceReportingId` forward purely as a lightweight traceability link. The Historique list page renders a small "Rectifié" tag on any row where that link is present, and now sorts by period (ascending) rather than by send date.

This directly implements the 2026-08-20 squad sync's reversal of the earlier (2026-08-19) plan to keep every transmission in Historique with a distinct "Annulé" status on superseded ones. No "Annulé" status was ever built in code, so no cleanup was needed there — just the correct replace-in-place behavior on `transmit()`.

### 3. Direct navigation to the rectificatif after creation

When a rectificatif is created (or updated) from an already-transmitted reporting's invoice drawer, the user is now navigated straight to the rectificatif's own detail view instead of back to the "À transmettre" list — so the diff (deleted line + all carried-over lines) is visible immediately, per the squad sync's explicit UX requirement.

### 4. Read-only lock + "rectificatif en cours" banner on the original

Added a computed lookup (`openRectificatif`) on the detail page: for the reporting currently displayed, it searches the full reportings list for any other reporting whose `sourceReportingId` points back to it and whose status is still `to-rectify`. This works uniformly for achats (whose own status stays "Transmis" while a rectificatif is open) and ventes (whose own status flips to a new "rectifying" / "En cours de rectification" state), without needing the two flows to be visually consistent first.

When a linked open rectificatif is found: a caution banner appears on the reporting ("Rectificatif en cours pour cette période... en lecture seule") with a "Voir le rectificatif" button linking to it; the bulk-selection column disappears for a locked ventes reporting; and the invoice drawer's "Supprimer" action (achats Public-API-sourced invoices, and ventes) is replaced by a "Verrouillée — rectificatif en cours" message. A new `readOnly` input was added to the invoice-drawer component for this.

### 5. Rejected corrections moved out of Historique

Per the squad sync's rule ("rejected corrections stay in à transmettre tagged à rectifier, and never enter history"), the three mock reportings that previously sat in Historique with status "rejected" (two achats, one paiements) were converted to status `to-rectify` and relocated into the "À transmettre" section of the mock data (renamed from `hist-4`/`hist-7`/`hist-8` to `rec-10`/`rec-11`/`rec-12`). The History page's status filter no longer includes "rejected". The generic `rejected` status value and its other consumers (a DGFiP-rejection timeline branch, back-navigation routing) were deliberately left in the codebase as valid but currently-unexercised — they weren't broken, just unused by current mock data.

## What is still open (not implemented)

- **Manual "cancel this rectificatif" action.** The squad sync specified V1 = manual deletion of a draft rectificatif by the user (not automatic, unlike the target vision gated on a future Cegedim delete-project endpoint). No such action exists yet in the prototype — a rectificatif can only be transmitted, never explicitly cancelled.
- **Achats/ventes inconsistency on the visual "in progress" status.** Ventes flips the original's status to "rectifying" while a correction is drafted; achats leaves its own status at "Transmis" throughout. The read-only lock (item 4 above) works correctly either way since it doesn't depend on this status field, but the two source channels still look inconsistent to a user comparing them side by side.
- **Terminology cleanup.** The squad sync's action item for Fabien Riou ("clean up prototype wording/tags, e.g. 'modifié', 'supprimé', 'en cours', based on session feedback") is still open — no specific replacement wording was given in the meeting notes beyond "prefer 'reporting précédent' over 'initial'", which hasn't yet been applied to the prototype's UI copy or code comments.
