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

## [2026-09-10] refactor | Remove all Agicap-scoped content — wiki now scoped to Ouch!/FixMyLife only

- Removed: entities `Ludovic_Lelievre.md`, `Audric_Podmilsak.md`, `Paul_Sorrentino.md`, `Cegedim.md`; concepts `E-Reporting_Rectificatif.md`, `Reporting_Period.md`, `FRR_Flow.md`, `DGFIP_PPF.md`, `Public_API_Invoice_Ingestion.md`, `B2C_Manual_Entries.md`, `Period-Correction_Bundling.md`; MOC `MOC_E-Reporting_Rectificatif.md`; syntheses `syntheses/meetings/2026-08-20_e-reporting-rectificatif-squad-sync.md`, `syntheses/projects/2026-08-21_rectification-achats-v2-implementation-progress.md`, `syntheses/projects/2026-08-26_rectification-achats-v2-period-correction-bundling.md`; raw sources `raw/transcripts/2026-08-20_e-reporting-rectificatif-squad-sync.md`, `raw/articles/2026-08-21_rectification-achats-v2-implementation-update.md`, `raw/articles/2026-08-26_rectification-achats-v2-period-correction-and-ux-fixes.md`
- Updated: `wiki/index.md` (dropped all Agicap rows/MOC), `CLAUDE.md` (removed Agicap from About Me, dropped the two-context note, Glossary now Ouch!-only), `README.md` (genericized two Agicap-specific lines), scaffolding templates (`wiki/concepts/_template.md`, `wiki/concepts/README.md`, `wiki/entities/Example_Person.md`, `wiki/concepts/Example_Concept.md`) reworded from "Agicap" to "Ouch!/FixMyLife"
- Kept as-is (immutable raw source, historical record): `raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md` still mentions the day job in passing
- Ran `wiki/backlinks.py` after removal to clear stale "Referenced by" blocks

## [2026-09-10] install | Ouch! agent team — 9 product-design skills

- Source: uploaded bundle `ouchequipeskillscomplete.md` (9 SKILL.md files concatenated)
- Created: `skills/ouch-ceo/SKILL.md`, `skills/ouch-growth-hacker/SKILL.md`, `skills/ouch-cto/SKILL.md`, `skills/ouch-ux-designer/SKILL.md`, `skills/ouch-cfo/SKILL.md`, `skills/ouch-legal/SKILL.md`, `skills/ouch-persona-victime/SKILL.md`, `skills/ouch-persona-maker/SKILL.md`, `skills/panel-ouch-double-face/SKILL.md`
- Updated: `CLAUDE.md` — new "Ouch! Agent Team (skills)" section listing all 9 with role summaries
- Not a wiki-ingest (no new entity/concept/synthesis) — this is skill installation, tracked here for traceability since it changes how future sessions operate on this repo

## [2026-09-11] strategy | 90-day launch plan (CEO session)

- Source: live audit of the Lovable project `fix-it-karma` (files, Supabase tables, message history 2026-09-10/11) + existing wiki context; no new raw file (audit facts are recorded in the synthesis itself)
- Created: `wiki/syntheses/strategy/2026-09-11_launch-plan-90-days.md`
- Updated: `wiki/mocs/MOC_Ouch_FixMyLife.md` (linked the plan, added a build-state delta section, settled two open questions, added one), `wiki/index.md` (Strategy table)
- Key audit finding: all engagement data (votes, leads, voices, survey answers, submitted problems) is still `localStorage`; Supabase only has `profiles`. The `/communaute/independants` page must not be shared externally until shared persistence ships.
- Decisions logged: D1 persistence first (2-week cap) · D2 "concerné(e)s" final for launch · D3 launch surface = `/communaute/independants` · D4 no paywall before Cercle 2 signal · D5 feature freeze · D6 curated seeding (60 cards), scraping feeds a manual queue only
- Patterns: none — single planning session.
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] decision | Lovable ↔ GitHub connected, persistence spec written

- Decision: keep Lovable for preview/hosting/AI gateway, work on the code from GitHub (`xeonfab/fix-it-karma`, two-way sync on `main`). Full exit from Lovable deferred to after the day-90 decision (solves no cold-start, ~1 week of infra).
- Audit addition: the catalog carries demo counters/statuses/updates/verbatims and a synthetic growth curve; all removed at migration so makers never see an invented number.
- Created (app repo, branch `claude/persistence-spec`): `docs/persistence-spec.md` — schema (7 tables, 3 aggregate views), insert-only RLS for anonymous visitors, device-id identity without login, unchanged `useEngagement` contract, events + `?c=` channel tag, seed procedure, rollout order, acceptance criteria, ~21h estimate.
- Updated: launch plan (audit table, next-steps table), MOC (build-state delta).

## [2026-09-11] build | Phase 1 persistence implemented on `xeonfab/fix-it-karma` (branch `claude/persistence-spec`)

- Applied migration `20260911150000_shared_persistence.sql` on the Lovable Cloud database: 7 tables (`problems`, `votes`, `leads`, `voices`, `confirmation_votes`, `survey_answers`, `events`), 3 aggregate views, insert-only RLS for anonymous visitors, explicit revokes (Supabase default privileges had granted ALL to `anon`; verified as role `anon` that raw leads are now unreadable and duplicate votes are rejected).
- Seeded the 38 catalog cards with zero counters, status `incubation`; two syntheses with invented figures (ids 1 and 8) rewritten as neutral editorial notes.
- Client: `engagement.tsx` rewritten on react-query (optimistic writes, local mirror of ids only, unchanged hook contract), demo catalog moved to `src/lib/seed-catalog.ts` (seed script only), fake hero badge/statuses/maker updates/verbatims/seed voices/synthetic growth curve removed, live feed on real data, survey and duplicate detection on Supabase, `events` instrumentation with `?c=` channel tag, `docs/metrics.sql` for the Sunday review.
- Verification: typecheck and production build green, changed files prettier/eslint clean (main itself has 322 pre-existing prettier errors). The two-device browser test could not run in the sandbox: the Supabase host is denied by the session's network policy. Left for Fabien on the Lovable preview after merge.
- Updated: launch plan next-steps table.

## [2026-09-11] ingest | Founder's strategy voice note → community-by-community rollout playbook

- Source: `raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md` (dictated voice note, saved verbatim)
- Created: `wiki/syntheses/strategy/2026-09-11_community-rollout-playbook.md` — the long-run loop (ship → one community → channel map → problem submission → store/structure → makers → automate → replay), channel-type table for French freelances, automation ladder (levels 0–3, never auto-publish), replay kit checklist
- Updated: `wiki/mocs/MOC_Ouch_FixMyLife.md` (linked the playbook, new open question on "collecting organisations"), `wiki/index.md` (Strategy table), launch plan (Related pages)
- No new decision: the six launch-plan decisions stand. New open question: whether "organisations capables de recueillir les problèmes" means relay partners (collectives, coworkings, platforms) or the product's entités — default relay partners, bounded by hard rule 5
- Patterns: none (single source)
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] clarify | "Collecting organisations" = the product's entités; two maker profiles

- Source: `raw/transcripts/2026-09-11_strategie-entites-et-makers.md` (second dictated voice note, saved verbatim)
- Settled: the organisations that collect problems are the entités (companies, local authorities, public names). A problem tied to an entity must appear publicly on the dedicated entity page/listing. Makers = entrepreneurs and intrapreneurs: inside the entity (Type B) or independent people/collectives (Type A). Hard rules 4–5 (no special status, no outreach) unchanged.
- Updated: rollout playbook (both-sides section, open question struck through, next-steps table), MOC (open question settled), `wiki/index.md` (row summary)
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] deliverables | Freelance push — deck, channel plan, structure/dedup spec

- Trigger: Fabien asked the whole team to advance on Cercle 1 (freelances) on three fronts: quality problem cards collected from the channels, a communication strategy per channel to get problems submitted, and platform design for clean presentation and a duplicate-free, unambiguous database.
- Source: live read of `xeonfab/fix-it-karma` (qualify prompt, duplicate detection, entities, problems, submit flow, community page, persistence spec) and of the Lovable Cloud database (7 tables, 38 seed rows). No new raw file: facts are recorded in the pages.
- Created: `wiki/syntheses/projects/2026-09-11_freelance-deck-v1.md` (+ `.csv` export, 54 rows), `wiki/syntheses/strategy/2026-09-11_freelance-channel-communication-plan.md`, `wiki/syntheses/projects/2026-09-11_problem-structure-dedup-spec.md`
- Updated: `wiki/index.md` (3 rows), MOC (new "Freelance push" section, 2 open questions), launch plan (next-steps table)
- Key audit findings: community deck hard-coded by ids (submitted freelance cards never reach the freelance page); 18 of 31 entities are placeholders linked by 24 seed cards; duplicate check limited to one sector·topic and 40 rows; `topic_hashtag` null on all seeds; seed id 1 title/statement mismatch; submitting requires Google login and the wall is unmeasured.
- Decisions proposed (not yet settled by Fabien): retire placeholder entities; add `communities` tag; measure the login wall before any anonymous-publication decision; canonical merge instead of deletion.
- Patterns: none.
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] team | Skills audit — 9 updated, 3 created, auto-trigger defect fixed

- Trigger: Fabien asked whether the team is the most expert one for the freelance objective and to update/create skills where not.
- Defect: all 9 Ouch! skills (and `wiki-clean`) declared `description: >` folded blocks that the loader does not surface, so no natural-language trigger could fire. Rewritten as single-line quoted descriptions, content unchanged.
- Updated: `ouch-ceo` (D1–D6, rollout loop, gates, Sunday rule, experts to convene; former-employer reference removed), `ouch-cto` (real stack: Supabase live, GitHub sync, one driver; fragile list; dedup and registry doctrine), `ouch-growth-hacker` (Cercle 1 playbook: waves, etiquette, login wall, proxy submission, harvest), `ouch-legal` (registry rules, sourcing sheet, harvest rewriting, hashtag, entity-page nevers), `ouch-ux-designer` (community/entity page rules), `ouch-persona-victime` (+Sami), `ouch-persona-maker` (+Nadia), `panel-ouch-double-face` (guest seat), `ouch-cfo` (front-matter only)
- Created: `skills/ouch-expert-independants/SKILL.md`, `skills/ouch-editeur-cartes/SKILL.md`, `skills/ouch-data-analyst/SKILL.md`
- Wiki: `wiki/syntheses/strategy/2026-09-11_team-skills-audit.md` (coverage matrix, what was not created and why), `CLAUDE.md` team table (12 rows), index, MOC
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] review | Expert pass on the freelance deck (ouch-expert-independants)

- Created: `wiki/syntheses/projects/2026-09-11_freelance-deck-v1_expert-review.md` — 54 cards checked (mechanism, figure, entity, Type A/B, frequency)
- Corrected in the deck and CSV: F03 (60 jours fin de mois exceeded the legal cap → 60 jours), F08 (recovery cost is time, not money), F16 (client terms are conditions d'achat, hashtag `#ConditionsDAchat`), F35 (compte dédié vs compte pro); F22 title tightened
- Launch deck confirmed: nine large frictions plus the Qonto entity-page test
- Updated: deck page next steps, team audit next steps, index
- Ran `wiki/backlinks.py` after writing.

## [2026-09-11] build | Cercle 1 structure + freelance deck on `xeonfab/fix-it-karma` (branch `claude/freelance-deck-structure`)

- Applied live on the Lovable Cloud database: `20260912090000_community_structure` (extensions `pg_trgm`/`unaccent`, columns `communities`, `channel`, `deck_rank`, generated `norm_text`, banned-word check constraint with a « nulle part » exception, `similar_problems` RPC) and `20260912090100_freelance_deck_v1` (19 placeholder entities unlinked from 24 rows, hashtags on the 30 remaining seeds, cards 1 and 34 rewritten, 46 new cards; F20/F22 unpublished pending their source). Verified: 84 cards, 82 published, 54 tagged `independants`, 10 with a deck rank, 12 real entities left, no published pair above 0.6 similarity.
- Client: community page reads the tag via `communityDeck()` (pain → curated rank → recency, 48 h slot for fresh submissions), submit block below the deck, submissions carry `communities` + `channel`, four funnel events, share links to the community deck, `detectDuplicate` runs the trigram RPC across the whole table before the LLM judge, entity registry reduced to real organisations with aliases fed to the qualification prompt.
- Found and repaired: `main` did not typecheck — the persistence merge (`e3fe6e7`) had mangled the flip card in `swipe-deck.tsx`. Rebuilt from Lovable's complete version, `voteFor` added to the engagement provider.
- Not verified: `vite build` and the browser test. The sandbox's network policy blocks Lovable's private npm registry (`*.pkg.dev` 403), so `motion`, `@supabase/supabase-js` and `@lovable.dev/cloud-auth-js` could not be installed; a registry switch was refused by the permission classifier. ESLint clean on changed files; typecheck clean once those three packages are stubbed.
- Next: Fabien merges the branch (Lovable only sees `main`), runs the two-device test, logs the source for F20/F22.
- Updated: launch plan, MOC, spec, deck page.

## [2026-09-11] merge | PR #3 (deck + structure) and PR #2 (Lovable exit) both on `main` of `fix-it-karma`

- Fabien merged `claude/freelance-deck-structure` (PR #3, `8d5a717`). A parallel Claude session had pushed the Lovable exit on `claude/persistence-spec` (commit « Leave Lovable » `c1eac4c` + a second repair of the swipe card `98b0170`); merged as PR #2 (`ad33d7d`) on top, with a merge of `main` (`83368a9`). Verified on `main`: both sets of changes present (communities tag, similarity RPC, funnel events, entity aliases; Vite/Nitro Vercel preset, native Supabase auth, Claude API `claude-opus-5`, npm lockfile, `docs/deploy.md`). No placeholder slug left in code.
- Consequence recorded: the public URL `fix-it-karma.lovable.app` still serves the old build on the old Lovable Cloud database (38 seeds, no new column). Nothing to share until Fabien configures Vercel (`docs/deploy.md` §1) and runs the two-device test there.
- Updated: MOC (build-state delta), launch plan (audit row + next steps), `skills/ouch-cto/SKILL.md` (stack after the Lovable exit, two-sessions rule).
