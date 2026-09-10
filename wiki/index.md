# 📇 Wiki Index

> Catalog of all wiki pages. Claude consults this file first to navigate.
> Updated automatically at each ingest.

---

## 🗺️ Maps of Content (MOC)

Thematic entry points — curated navigators across entities, concepts, syntheses. See [`mocs/README.md`](mocs/README.md).

| Map | Scope |
|---|---|
| *(add your first MOC once you have 3+ related pages — e.g., Payments, E-invoicing, Your_Key_Project)* | — |
| [E-Reporting Rectificatif](mocs/MOC_E-Reporting_Rectificatif.md) | Corrective VAT e-reporting on purchase invoices — object model, rollout sequencing, target-vision answer to the cross-period duplicate-declaration risk |

---

## 👥 Entities

### People — Leadership
| Page | Summary |
|---|---|
| *(e.g., your manager, your CEO)* | — |

### People — Your squad(s)
| Page | Summary |
|---|---|
| *(e.g., PMs, devs, designers you work with)* | — |
| [Ludovic Lelievre](entities/Ludovic_Lelievre.md) | Functional lead on e-reporting rectificatif — delivery sequencing |
| [Audric Podmilsak](entities/Audric_Podmilsak.md) | Engineering perspective on e-reporting rectificatif — technical cost, AP-first strategy |
| [Paul Sorrentino](entities/Paul_Sorrentino.md) | UX/product sanity-check on e-reporting rectificatif — consistency with initial reporting |

### Organisations & banks
| Page | Summary |
|---|---|
| *(e.g., competitors, partners, clients)* | — |
| [Cegedim](entities/Cegedim.md) | PDP/intermediary partner platform between Agicap and DGFIP/PPF |

### Clients
| Page | Summary |
|---|---|

---

## 📚 Concepts

| Page | Summary |
|---|---|
| *(e.g., EBICS, pain.001, SEPA — technical or business concepts in your scope)* | — |
| [E-Reporting Rectificatif](concepts/E-Reporting_Rectificatif.md) | Corrective VAT e-reporting that replaces a previously-transmitted period once accepted |
| [Reporting Period](concepts/Reporting_Period.md) | The SIREN + date-range unit a rectificatif always targets |
| [FRR Flow](concepts/FRR_Flow.md) | The e-reporting file generated and sent to Cegedim per period |
| [DGFIP / PPF](concepts/DGFIP_PPF.md) | French tax administration and its public invoicing portal — final destination of e-reporting |
| [Public API Invoice Ingestion](concepts/Public_API_Invoice_Ingestion.md) | AP-client channel pushing invoice create/update/delete directly to Agicap |
| [B2C Manual Entries](concepts/B2C_Manual_Entries.md) | Manually-entered B2C transactions/payments — third source channel for e-reporting |
| [Period-Correction Bundling](concepts/Period-Correction_Bundling.md) | Transmitting every rectificatif born from the same period correction as one action, to avoid a DGFiP duplicate-declaration risk |

---

## 🔍 Patterns

| Page | Confidence | Scope | Summary |
|---|---|---|---|
| [Example Pattern](patterns/Example_Pattern.md) | 🟡 moderate | AP · France · Enterprise | Example pattern page — delete once comfortable |

---

## 📝 Syntheses

### 🗓️ Meetings & calls (`meetings/`)
| Page | Date | Summary |
|---|---|---|
| *(e.g., `meetings/2026-04-15_weekly-pa.md`)* | — | — |
| [E-reporting rectificatif — squad sync](syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md) | 2026-08-20 | Object model, UX, and phased delivery plan for corrective e-reporting on purchase invoices |

### 🏢 Competitors (`competitors/`)
| Page | Summary |
|---|---|

### 🎯 Strategy (`strategy/`)
| Page | Summary |
|---|---|

### 🚀 Projects (`projects/`)
| Page | Summary |
|---|---|
| [Rectification-achats-v2 — implementation progress](syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md) | Prototype now builds the 2026-08-20 squad sync's object model, Historique redesign, and read-only lock — manual rectificatif cancellation and achats/ventes visual consistency still open |
| [Rectification-achats-v2 — period-correction bundling](syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md) | Transmis/Accepté status split, UX fix batch, and the target-vision bundled-transmission design/prototype for the cross-period duplicate-declaration risk |

### 🔬 Research (`research/`)
| Page | Summary |
|---|---|
