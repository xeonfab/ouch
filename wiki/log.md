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

## [2026-09-11] validate | Merged `main` of `fix-it-karma` builds

- With the Lovable registry gone (npm lockfile), dependencies install from the public registry: `npm ci` ok, `npx tsc --noEmit` exit 0, `npm run build` exit 0 (`.vercel/output` generated, Nitro preset vercel). `npm run lint`: 66 prettier formatting errors on files untouched by both PRs (pre-existing), no logic error.
- Not runnable here: the browser two-device test (the sandbox's network policy blocks `*.supabase.co` and the Vercel/Lovable hosts). Left to Fabien on the Vercel deployment.

## [2026-09-11] ci | Guard rail on `fix-it-karma` main (branch `claude/ci-and-format`)

- Fabien asked whether everything could be done without him. Honest split: Anthropic key, Google OAuth client, Vercel project and the Lovable disconnect need his accounts (no connector exists for them in this session; `ListConnectors` confirms). Everything else done.
- Added `.github/workflows/ci.yml` (npm ci, tsc, lint, build on pushes to main and on pull requests), formatted the tree with the project's prettier (formatting only, lint now exits 0), ignored `.vercel`/`.output`. Typecheck, lint and build green; branch pushed, to merge.

## [2026-09-12] deploy | Vercel live, first field check

- Fabien deployed `fix-it-karma` on Vercel (Hobby, `fix-it-karma.vercel.app`, source `main` `ad33d7d`). Vercel runtime logs: every page 200 (`/`, `/communaute/independants`), zero errors; the « This page didn't load » thumbnail is not reproduced (the generated Vercel function rendered all pages locally, with and without env vars) and is treated as a stale first-request capture.
- Field anomaly: after Fabien's visits, `events`, `votes`, `survey_answers` still count 0 in the `ouch` database, while the local headless-browser check shows the client does issue the Supabase requests (problems, stats, voices, `community_visit`). Verified: the publishable key embedded in the build matches the project's active key; the anon role can read problems/stats, call `similar_problems` and insert events. Cause not identifiable from the sandbox (browser side); asked Fabien for the browser console and a swipe.
- Branch `claude/ci-and-format` (to merge) also adds an explicit loading state and a failure state with retry on the swipe deck (it previously showed « Tu as tout passé en revue ! » when the registry could not load), plus a migration pinning `search_path` on the two SQL functions (Supabase advisor), applied live.
- Note for Fabien: the Vercel « Environments » page is not where env vars go; it is Settings → Environment Variables.

## [2026-09-12] debug | Error page on the Vercel deployment, cause not yet identified

- Fabien sees « This page didn't load » on `/communaute/independants?c=test` while Vercel logs the request as 200: the crash is client-side. Reproduced neither with blocked network nor with the real 82 rows injected into headless Chromium (page renders, deck 1/10). Suspects: browser-specific (Mac user agent, Safari?) or the auth call path, which the sandbox cannot exercise.
- Branch `claude/ci-and-format` now makes the error page print the error message and record a `client_error` event (message, stack, path, user agent) so the next reload gives the exact cause in the database. Same branch: swipe deck honours the curated id order (it followed registry order before).
- Next: Fabien merges the branch, reloads; I read `events where name = 'client_error'`.

## [2026-09-12] fix | Root cause of the Vercel error page: no environment variables in the build

- Fabien's screen showed « Missing Supabase environment variable(s): SUPABASE_URL, SUPABASE_PUBLISHABLE_KEY ». The Vercel build did not embed the public Supabase values (the committed `.env` was not picked up, and the six variables were not yet set in Vercel), so the browser client threw at start.
- Fix on `claude/ci-and-format`: the public URL and publishable key now fall back to their public values in the client, the auth middleware and the server client; the two secrets keep no fallback. `docs/deploy.md` records the incident. Setting the variables in Vercel (Settings → Environment Variables) remains required for the secrets.

## [2026-09-12] deploy | PR #4 merged without the fallback; PR #5 opened

- Fabien merged `claude/ci-and-format` as PR #4 (`4181f44`) before the fallback commit landed on the branch; the deployed error page now prints the exact message (« Missing Supabase environment variable(s): SUPABASE_URL, SUPABASE_PUBLISHABLE_KEY »), confirming the diagnosis. `client_error` events cannot land in that state (the Supabase client itself fails to build).
- Opened [PR #5](https://github.com/xeonfab/fix-it-karma/pull/5) (`claude/supabase-public-fallback`, cherry-pick of the fallback commit on top of main); subscribed to its activity to drive CI to green.

## [2026-09-12] merge | PR #5 merged: Supabase public fallback on `main`

- CI green (first run of the new workflow), Vercel preview ready, merged by Fabien at 00:23 UTC. Production redeploys from `main`; the error page cannot recur for missing public values. Remaining for Fabien: the two server secrets in Vercel (problem submission, duplicate detection), then the two-device test.

## [2026-09-12] field | Production works end to end; sourcing sheet; channel map v0; one bug found

- Fabien confirmed the site works after PR #5. Database at 00:40 UTC: 31 events on `?c=test` from one device (14 right swipes, 2 left, 7 Google opt-ins, 3 `submit_started`, 1 `submit_login_wall`, 1 problem published through the Claude qualifier). Leads, votes and events all land; the login wall was hit once then passed.
- Bug found in the field: the submitted card (id 86) has an empty `communities` tag. After the Google redirect the submit modal reopens from the saved draft without the open event, so the community prop is lost. Fixed on branch `claude/submit-community-persist` (draft carries the community). Also noted: the qualifier filed a blocked-account card under « Paiements partagés » (taxonomy v2 case) and did not tag Qonto (chip not confirmed); similarity to card 36 is 0.35, so L1 surfaced it; the judge or Fabien kept it separate.
- Sourcing sheet written (`wiki/syntheses/research/sourcing-sheet-entity-cards.md`) for the seven entity-named cards from public sources; F20 and F22 published in the database.
- Channel map v0 written (`wiki/syntheses/strategy/2026-09-12_freelance-channel-map.md`): named Facebook groups, two Slack communities, Free-Work forum, Services Publics+ as harvest source; sizes and rules unverified (community pages unreachable from the sandbox), proposal for the three waves.
- Open for Fabien: second-device test; decide whether the `?c=test` rows (his own votes, leads and card 86) are purged before the first wave (proposed SQL in the plan is not run without his say).

## [2026-09-12] pr | PR #6 opened: community tag survives the Google sign-in

- [PR #6](https://github.com/xeonfab/fix-it-karma/pull/6) (`claude/submit-community-persist`), subscribed for CI. Once merged, cards submitted from `/communaute/independants` carry `communities = {independants}` even when the visitor signs in with Google mid-flow.

## [2026-09-12] merge | PR #6 merged: community tag survives the sign-in round-trip

- CI green, merged at 00:50 UTC. From this deployment on, a card submitted from `/communaute/independants` carries `communities = {independants}` even after the Google redirect. Card 86 (Fabien's test) keeps its empty tag; purge or tag it manually if it is kept.

## [2026-09-12] pr | PR #7 opened: vote button becomes a call to action, author line moved

- Fabien's field review of `/communaute/independants` on 2026-09-12 raised two points: the vote pill on cards (grey `🔥 0`) read as a counter, so visitors did not know they could vote; and "Vous publiez en tant que X" above the write headline was useless at that moment.
- UX decisions (ouch-ux-designer): the vote is now a coral `Moi aussi 🔥` button (mint `Toi aussi ✓` once voted), count hidden at zero; in exchange the `douleur /100` number leaves the victim-side card, it belongs to the maker register and was 0 on most fresh cards. The author line moves to a one-line note under the publish button (the name is public on the card, so it is stated where it matters).
- [PR #7](https://github.com/xeonfab/fix-it-karma/pull/7) (`claude/ux-card-vote-cta`), subscribed for CI. Card standard rule to carry into the presentation section of the dedup spec: one number per victim-side card, the one the visitor can move.

## [2026-09-12] merge | PR #7 merged: vote button is a call to action, author line moved

- Merged at 01:01 UTC, CI green. Live from this deployment: victim-side cards show « Moi aussi 🔥 » (count hidden at zero) instead of the grey counter and the `douleur /100` number; the write step no longer shows « Vous publiez en tant que », the signature note sits under the publish button.
- To watch in the events table from now on: `vote` rows with `source = card` (listing) versus the swipe, to see whether the button moves the vote rate on the ranked list.

## [2026-09-12] pr | PR #8 opened: ranked lists frozen during the visit, card votes tagged

- Fabien's test after PR #7: voting « Moi aussi » on card 42 made it jump to rank 37, because the listing is sorted by Score de Douleur and re-sorted live. Rule added to the presentation section of the dedup spec: a ranked list never re-sorts under the visitor's cursor; the order is computed once per page load (`useFrozenOrder`), new cards go first.
- Card votes now carry `source = card` in the event props (they defaulted to `swipe`); the log entry of PR #7 assumed this and was wrong until PR #8 is live. Also `.vercel` added to eslint ignores.
- [PR #8](https://github.com/xeonfab/fix-it-karma/pull/8) (`claude/card-vote-source`), subscribed for CI.

## [2026-09-12] merge | PR #8 merged: ranked lists frozen for the visit, card votes tagged

- Merged at 01:16 UTC, CI green. Live: the community listing and the home « Tendances » keep their order while the visitor votes; card votes carry `source = card` in `swipe_right` events, so query 9 of `docs/metrics.sql` can split card votes from swipe votes from this deployment on.
- Open UX question from Fabien: list view instead of the card grid for reading the ranked problems. Verdict given with a mock (list on the community listing and the catalogue, cards kept on the swipe and on the home showcase); waiting for his call before building `ProblemRow`.

## [2026-09-12] pr | PR #10 and PR #11 opened: stale-chunk reload, list view for reading

- Fabien hit « Failed to fetch dynamically imported module » on a tab open across the PR #8 deployment. [PR #10](https://github.com/xeonfab/fix-it-karma/pull/10) (`claude/stale-chunk-reload`): the root error boundary recognises the stale-chunk error family and reloads once per URL (sessionStorage guard), Vite's `vite:preloadError` handled the same way, no `client_error` event for these.
- Fabien said « oui go sur liste ». [PR #11](https://github.com/xeonfab/fix-it-karma/pull/11) (`claude/problem-list`): `ProblemRow`/`ProblemList` on the community listing and the catalogue; sector chip and topic leave the rows; catalogue drops the maker-style table and the leads sort; `useFrozenOrder` takes a reset key so a chosen sort or filter re-ranks while a vote does not; list votes carry `source = list`. Cards stay on the swipe and the home showcase.
- Rule for the spec: the victim side has two objects, the card (decision, one at a time) and the row (reading, ranked); the Terminal keeps its table.

## [2026-09-12] merge | PR #10 merged: stale-chunk reload

- Merged at 01:21 UTC, CI green. A tab open across a deployment now reloads itself once instead of showing « Failed to fetch dynamically imported module ».

## [2026-09-12] merge | PR #11 merged: list view on the community listing and the catalogue

- Merged at 01:22 UTC, CI green. Live: « Déjà signalé par la commu » and the catalogue read as one line per problem with the vote button in the right column; cards remain on the swipe and the home showcase. Votes from the list carry `source = list`, from the home cards `source = card`, from the deck `source = swipe`.
- State of the day: PRs #7, #8, #10, #11 merged in one evening on Fabien's field feedback (vote CTA, frozen ranking, stale-chunk reload, list view). Next on Fabien's side: phone test, friends wave `?c=amis`, decision on purging `?c=test`. Next on mine: weekly metrics sheet (`ouch-data-analyst`), card 86 moderation.

## [2026-09-12] pr | PR #12 opened: a visitor can take back their own vote

- Fabien, on the list view: a mis-click on « Moi aussi » had no way back. [PR #12](https://github.com/xeonfab/fix-it-karma/pull/12) (`claude/retract-vote`): the mint « Toi aussi ✓ » button retracts the vote (list rows and home cards), counter drops at once, `vote_retracted` event with source and direction.
- Database: `retract_vote(problem_id, device_id)` applied live (security definer, search_path pinned, anon + authenticated). Deletes only that device's vote; the device uuid acts as the token. Votes are not content, so this does not touch the no-deletion rule for cards; the trace stays in `events`.
- Not covered: undoing a swipe in the deck (a different gesture, « annuler » on the last card), to design if the field asks for it.

## [2026-09-12] merge | PR #12 merged: a visitor can take back their own vote

- Merged at 01:30 UTC, CI green. Live: the mint « Toi aussi ✓ » button retracts the vote on list rows and home cards; `retract_vote` RPC in place; `vote_retracted` events carry source and direction.

## [2026-09-12] project | Next bricks after « go prochaines briques »: metrics sheet, legal review, plan update

- **Weekly metrics sheet** created by `ouch-data-analyst` → [`2026-09-12_weekly-metrics-sheet.md`](syntheses/projects/2026-09-12_weekly-metrics-sheet.md), week 0 filled from the live database: 2 voting devices, 49 votes, 7 leads (1 email), 1 submission, 17 client errors all from the stale-chunk incident. Anomalies: the second device swiped on the generic `/swipe` (id order, not the curated deck), reachable from every header and footer; card 86 is a near-duplicate of 36 with wrong topic, empty tag and no entity. Queries 13–14 (vote sources, retractions) added to `docs/metrics.sql` in PR #13.
- **Legal pages review** by `ouch-legal` → [`2026-09-12_legal-pages-review.md`](syntheses/projects/2026-09-12_legal-pages-review.md): 9 gaps fixed in [PR #13](https://github.com/xeonfab/fix-it-karma/pull/13) (host named, LCEN non-professional clause, device id and usage events, Anthropic processor and transfer, legal bases, retention, CNIL, no-deletion wording, entities without status). Two facts left to Fabien: the contact address (`contact@ouch.example` is still a placeholder on all three pages) and the publisher identity choice.
- 90-day plan rows updated (metrics sheet done, legal pages reviewed, Vercel deployed, two devices tested); new open question on the generic `/swipe` leak from community pages.
- Recommendation on card 86 (`ouch-editeur-cartes`): keep 36 canonical; unpublish 86 with the `?c=test` purge, or fix its tag/topic/entity if Fabien wants to keep his test card visible. Not executed without his call.

## [2026-09-12] pr | PR #14 opened: « Swiper » keeps a community visitor on the community deck

- CEO call on the open question raised by the metrics sheet: during the friends wave, a visitor sent to `/communaute/independants` must stay on the curated deck. [PR #14](https://github.com/xeonfab/fix-it-karma/pull/14) (`claude/community-swipe-links`): header « Le Swipe » and footer « Swiper 👉 » point to the community page on community routes (`useSwipeTarget`), `/swipe` elsewhere; `community_visit` carries user agent and viewport width. Ranking the generic `/swipe` by Score de Douleur stays open.

## [2026-09-12] merge | PR #14 merged: « Swiper » keeps a community visitor on the community deck

- Merged at 01:44 UTC, CI green. Live: header and footer « Swiper » point to `/communaute/independants` on community routes; `community_visit` events carry user agent and viewport width.

## [2026-09-12] merge | PR #13 merged: legal pages reviewed, metrics queries 13–14

- Merged at 01:44 UTC, CI green. Live: mentions légales name the host and use the LCEN non-professional clause; confidentialité lists the device id, usage events, the Anthropic processor and transfer, legal bases, retention, rights and the CNIL; CGU state correction / merge / unpublication, vote retraction, entities without status. Placeholders left for Fabien: contact address, publisher identity.
- All PRs of the evening merged (#7, #8, #10, #11, #12, #13, #14). Nothing open in the app repo. Next: Fabien's contact address, card 86 and `?c=test` purge decisions, friends wave `?c=amis`; the Sunday metrics line.

## [2026-09-12] decision | Card 36 canonical, card 86 unpublished, field-test data purged

- Fabien: « garder la 36 canonique, dépublier la 86 avec la purge ». Executed live at 02:05 UTC: card 86 set `published = false` (row kept, no deletion); all engagement rows deleted since every row came from the evening's field test (3 devices: the Mac on `?c=test`, the phone direct at 01:00, and a third device on `?c=amis` at 02:01 identified as Fabien's Mac again by identical user agent, viewport and timing). Deleted: 54 votes, 8 leads, 124 events; confirmations and survey answers were empty. 85 → 84 published cards.
- Week 0 of the metrics sheet keeps the numbers as the record of the test; from now on the counters start at zero for the friends wave.
- Side effect: Fabien's browsers still hold the local vote mirror, so his cards show « Toi aussi » without a server row; clearing the site data (or retracting, which deletes nothing) resets them. Not an issue for new visitors.

## [2026-09-12] pr | PR #16 opened: the opt-in prompt follows every positive vote

- Fabien: « Moi aussi » in the list did not offer the email / Google opt-in, unlike the swipe. [PR #16](https://github.com/xeonfab/fix-it-karma/pull/16) (`claude/lead-prompt-everywhere`): shared `LeadPromptProvider` at the root; rows, home cards and the deck apply the same rules (Google user → silent lead; email given during the visit → reused; else one prompt per visit, then « Ajouté »). The deck loses its duplicated modal. Behaviour change: an email typed once now registers the visitor on the cards voted afterwards in the visit, as Google already did.
- Rule for the spec: every positive vote, wherever it happens, is followed by the same opt-in path; a vote surface without it is a leak.

## [2026-09-12] merge | PR #16 merged: the opt-in prompt follows every positive vote

- Merged at 02:09 UTC, CI green. Live: « Moi aussi » in the list and on the home cards opens the same Google / email prompt as the swipe (once per visit), Google users and visitors who gave an email are registered silently on the cards they vote for.
- Question from Fabien: other SSO besides Google? Answer given: none before the friends wave; next is an email magic link (Supabase OTP), not another provider; LinkedIn only on a field signal; Facebook, Apple, Microsoft, GitHub set aside. Decision pending the `submit_login_wall` reading on Sunday.

## [2026-09-12] pr | PR #17 opened: email magic link next to Google

- Fabien: « ok lien magique ». [PR #17](https://github.com/xeonfab/fix-it-karma/pull/17) (`claude/magic-link`): `signInWithMagicLink` (Supabase OTP, return to the current page), `SignInOptions` = Google then « ou par email », on the submission wall, the « joined » screen and behind « Rejoindre » in the header (now a dialog). Event `login_magic_link_sent` with source. Deploy doc: Supabase's default sender is development-only, custom SMTP via Resend + rate limit + French template required before the friends wave (Fabien, dashboard).
- Decision settled in the plan: sign-in = Google + magic link; LinkedIn only on a field signal; no Facebook / Apple / Microsoft / GitHub.

## [2026-09-12] merge | PR #17 merged: email magic link next to Google

- Merged at 02:15 UTC, CI green. Live: « Rejoindre », the submission wall and the « joined » screen offer Google then « ou par email ». The email itself only reaches visitors once Fabien sets custom SMTP (Resend) on the Supabase project, `docs/deploy.md` b bis.
- Evening total: PRs #7, #8, #10, #11, #12, #13, #14, #16, #17 merged on field feedback. Open on Fabien's side: SMTP setup, real contact address on the legal pages, friends wave `?c=amis`. Sunday: week 1 line of the metrics sheet.

## [2026-09-12] pr | PR #19 opened: community page decluttered on mobile

- Fabien's phone read (09:04): too loaded, complex description, « Spécial indépendants » lost in a chip, counters useless, heart less clear than « Moi aussi », swipe card should carry the list row's landmarks. [PR #19](https://github.com/xeonfab/fix-it-karma/pull/19) (`claude/mobile-declutter`): title = « Spécial indépendants 🧾 », one-line promise, « 1 / 9 » progress only, labelled pills « Passer » / « Moi aussi 🔥 », card front = emoji + hashtag + entity chip + first-person statement, one counter only above zero, register « tu ».
- Rules added to the spec: the swipe card front and the list row share the same landmarks (emoji, hashtag, entity, « Moi aussi »); the statement stays first person on the card, the title stays factual on the row; no counter at zero anywhere on the victim side; « tu » everywhere on the victim side.

## [2026-09-12] merge | PR #19 merged: community page decluttered on mobile

- Merged at 07:43 UTC, CI green. Live: « Spécial indépendants 🧾 » as the title, one-line promise, « n / N » progress only, labelled « Passer » / « Moi aussi 🔥 » pills, card front with the list row's landmarks and one counter only above zero, « tu » register.

## [2026-09-12] pr | PR #20 opened: being notified is a per-card choice

- Fabien on the phone: « Moi aussi » did not ask for his email (prompt already shown once in the tab), and he wants to choose card by card. [PR #20](https://github.com/xeonfab/fix-it-karma/pull/20) (`claude/notify-me-per-card`): first positive vote of a visit → skippable prompt; every vote after → toast « Ajouté ✨ » with a one-tap « Préviens-moi 🔔 » (no form when the email is known); bell on voted rows and home cards to ask later; silent registration of every vote for known emails (PR #16) removed, so « en attente d'une solution » counts explicit requests only.
- Rule replaces the PR #16 line in the spec: voting and being notified are two intents; the opt-in is offered after every positive vote, chosen per card in one tap, never applied silently.

## [2026-09-12] merge | PR #20 merged: being notified is a per-card choice

- Merged at 07:59 UTC, CI green. Live: skippable prompt on the first vote of a visit, then « Ajouté ✨ » toast with a one-tap « Préviens-moi 🔔 » per card, bell on voted rows and home cards, no silent registration.
- Morning total on Fabien's phone feedback: PRs #19 and #20 merged. Open on Fabien's side: SMTP Resend, contact address, friends wave `?c=amis`. Sunday: week 1 line.

## [2026-09-12] pr | PR #21 opened: entity page reduced to number + list + maker banner

- Fabien on `/entite/urssaf-auto-entrepreneur`: still too much noise. Note: another session had merged a folded entity page this morning (three detailed cards, two stat tiles, `entity_page_visit` event). [PR #21](https://github.com/xeonfab/fix-it-karma/pull/21) (`claude/entity-page-declutter`): header = emoji, `#Name`, one muted line; capturable number only (card count with a vote nudge when no vote yet, never a big zero; leads as one small line above zero); every card as a `ProblemList` row, ten visible then folded; no status / resolution / score / author / voices on the rows; « Swiper d'autres problèmes » gone (footer has it); maker banner kept.
- Rule confirmed in the spec's entity page section: one number, one list of rows, one maker banner; the Terminal keeps the details.

## [2026-09-12] merge | PR #21 merged: entity page reduced to number + list + maker banner

- Merged at 08:15 UTC, CI green. Live on every `/entite/:slug`: header, capturable number (never a big zero), list rows, maker banner. Nothing else.
- Morning total on Fabien's phone feedback: PRs #19, #20, #21 merged. Open on Fabien's side: SMTP Resend, contact address, friends wave `?c=amis`. Sunday: week 1 line.
