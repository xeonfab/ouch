# 📜 Wiki Log

> Chronological journal of wiki operations. Append-only.
> Format: `## [YYYY-MM-DD] type | description`
> Types: `ingest`, `query`, `clean`, `refactor`

---

<!-- First entry will be appended here by the wiki-ingest skill on your first ingest. -->

## [2026-08-20] ingest | E-reporting rectificatif — squad sync (transcript, 2026-08-20)

- Source: `raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md`
- Created:
  - Synthesis: `wiki/syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md`
  - Entities: `wiki/entities/Ludovic_Lelievre.md`, `wiki/entities/Audric_Podmilsak.md`, `wiki/entities/Paul_Sorrentino.md`, `wiki/entities/Cegedim.md`
  - Concepts: `wiki/concepts/E-Reporting_Rectificatif.md`, `wiki/concepts/Reporting_Period.md`, `wiki/concepts/FRR_Flow.md`, `wiki/concepts/DGFIP_PPF.md`, `wiki/concepts/Public_API_Invoice_Ingestion.md`, `wiki/concepts/B2C_Manual_Entries.md`
- Updated: `wiki/index.md` (Entities, Concepts, Syntheses tables)
- Patterns: none created — two proto-patterns noted in the synthesis only (first occurrence, needs a second source to graduate to a full pattern page): (1) squad phases delivery by source channel before feature depth, (2) squad blocks/errors unresolved edge cases in V1 rather than solving them.
- No new MOC (user declined; fewer than 3 related pages so far per starter-pack convention, revisit later).

## [2026-08-21] ingest | Rectification-achats-v2 — implementation progress update (article, 2026-08-21)

- Source: `raw/articles/2026-08-21_rectification-achats-v2-implementation-update.md`
- Created:
  - Synthesis: `wiki/syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md`
- Updated:
  - `wiki/concepts/E-Reporting_Rectificatif.md` — Current status section revised from "🟡 Planned" to "🟢 In progress" with the implemented items listed and the remaining open ones split out; source link added; `last_reviewed` bumped
  - `wiki/concepts/Public_API_Invoice_Ingestion.md` — noted the prototype now demonstrates one possible answer to the previously-open "deleting a B2B invoice manually via this API" question (flagged explicitly as a prototype exploration, not a validated backend decision); source link added; `last_reviewed` bumped
  - `wiki/index.md` (Projects synthesis table)
- No new entities or concepts — this ingest is an implementation status update on existing pages, not new decisions or people.
- Patterns: none — no recurring signal observed here.
- No new MOC (still fewer than 3 unrelated clusters; revisit later).

## [2026-08-26] ingest | Rectification-achats-v2 — period-correction bundling and UX fixes (article, 2026-08-26)

- Source: `raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md`
- Created:
  - Synthesis: `wiki/syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md`
  - Concept: `wiki/concepts/Period-Correction_Bundling.md`
  - MOC: `wiki/mocs/MOC_E-Reporting_Rectificatif.md` (revisiting the earlier "fewer than 3 pages" deferral — now 3 syntheses + 5 concepts on this topic, clearly warranted)
- Updated:
  - `wiki/concepts/E-Reporting_Rectificatif.md` — Current status: added the Transmis/Accepté intermediate-status split, and a pointer to Period-Correction Bundling; source link added; `last_reviewed` bumped
  - `wiki/concepts/Reporting_Period.md` — nuanced the "cross-period blocked, not supported" line: still true for V1, but now explicitly framed as a deliberate pragmatic call with a target-vision design explored (not an unsolved/unsolvable risk); source link added; `last_reviewed` bumped
  - `wiki/concepts/DGFIP_PPF.md` — added the duplicate-declaration risk as a known risk in Current status, cross-linked to Period-Correction Bundling; source link added; `last_reviewed` bumped
  - `wiki/index.md` (MOC, Concepts, Projects synthesis tables)
- Patterns: none created — the "squad blocks unresolved edge cases in V1, revisits later as target-vision" proto-pattern (first noted 2026-08-20) has a second occurrence here (period correction specifically), but stays in the synthesis prose for now rather than becoming a full pattern page — same underlying topic evolving, not yet two independent sources.
- Ran `wiki/backlinks.py` after writing to refresh all "Referenced by" blocks.

## [2026-09-10] ingest | Ouch!/FixMyLife — full project context (spec, 2026-09-10)

- Source: `raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md`
- Created:
  - Synthesis: `wiki/syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md`
  - Concepts: `wiki/concepts/Score_de_Douleur.md`, `wiki/concepts/Resolution_Type_AB.md`
  - MOC: `wiki/mocs/MOC_Ouch_FixMyLife.md` (new topic cluster, distinct from the Agicap-scoped knowledge already in this wiki)
- Updated: `wiki/index.md` (MOC, Concepts, Projects synthesis tables), `CLAUDE.md` (About Me, Folder Map two-context note, Glossary, and a new "Ouch!/FixMyLife hard rules" section under Rules for Claude)
- No new entity pages — the 13-16 real-world entities named in the product (SNCF, Doctolib, Qonto, ...) are in-product content, not people/orgs Fabien interacts with; noted explicitly in the MOC instead.
- Patterns: none — single source so far for this topic, no recurring cross-source signal yet.
- Ran `wiki/backlinks.py` after writing to refresh all "Referenced by" blocks.
