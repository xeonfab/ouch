---
last_reviewed: 2026-09-11
---

# Ouch! — 90-day launch plan (CEO)

> One-line TL;DR: the single plan that takes Ouch! from "a polished prototype whose votes live in each visitor's browser" to "a live product with real shared votes, a first freelance audience, and a first maker signal" in 13 weeks at ~20h/week, with one priority per phase and a hard gate between phases.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | strategy |
| **Participants** | Fabien (founder), Karim (`ouch-ceo` skill) |
| **Source(s)** | Live audit of Lovable project `fix-it-karma` (2026-09-11), [full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md) |

---

## Context

The product surface is essentially built (swipe, Terminal Maker, entity pages, AI-assisted submission, legal pages, a dedicated `/communaute/independants` landing for Cercle 1). What has never happened is contact with a real audience. The constraint is not features or money; it is ~20h/week and a two-sided cold start. This plan freezes feature work, fixes the one thing that makes a public test meaningless, then spends the remaining weeks on distribution and on the first maker conversations.

## Audit — real state on 2026-09-11 (differs from the 2026-09-10 snapshot)

| Item | State | Consequence |
|---|---|---|
| Persistence of votes, leads, voices, submitted problems, confirmation votes | **`localStorage` only** (`src/lib/engagement.tsx`, key `ouch.engagement.v1`) | No two visitors see the same counter. The Score de Douleur, the "N concerné(e)s" counter, entity pages and the Terminal are all per-browser fiction. Any share to a real group loses 100% of the data. |
| Supabase | Enabled, but only a `profiles` table (Google SSO) | Auth exists; the data layer does not. |
| `/communaute/independants` (+ `/catalogue`) | Built 2026-09-10, includes a 2-question `CommunitySurvey` | The survey answers are also `localStorage` only (`ouch.survey.independants.v1`). **Do not share this link before Phase 1 ships.** |
| Google SSO after a positive swipe | Built | Good: cheaper opt-in than typed email. Keep. |
| Social share after publishing a problem | Built 2026-09-11 | Good: free distribution loop. Keep. |
| Lovable `roadmap.md` | All 12 items checked | Feature backlog is empty by design. Nothing else is "missing" for launch. |
| Demo counters in the catalog | `seedRight` up to 512, `seedLeads` up to 214, fake statuses, fake maker updates, fake verbatims, synthetic growth curve, hero "+12 480 problèmes" | **All zeroed or removed before any public share** (spec §1b). A maker must never see an invented number. |
| Code repository | `xeonfab/fix-it-karma` on GitHub; **Lovable exited on 2026-09-11** (PR #2): Vite/Nitro build for Vercel, native Supabase auth, Claude API for qualification and duplicates, npm lockfile | Claude Code works from the repo on branches, PR to `main` = Vercel deploy. Lovable's agent, preview and AI gateway are no longer part of the loop; the Lovable GitHub connection is to be disconnected per `docs/deploy.md` §3. |
| Vocabulary | Still "concerné(e)s" + 🔥 | Settled below (D2). |
| Legal pages `/mentions-legales`, `/confidentialite`, `/cgu` | Routes exist | Content to proofread once in Sprint 0, not rebuilt. |

## Decisions (settled, not to be re-litigated before day 90)

| # | Decision | Why |
|---|---|---|
| **D1** | **Shared persistence is the only build priority until it ships.** Minimal Supabase schema: `problems`, `votes`, `leads`, `voices`, `confirmation_votes`, `survey_answers`. Anonymous voting keyed by a device id stored client-side; **no login required to swipe**. Insert-only policies for anonymous visitors; aggregated reads through a view. Illustrations stay client-side (not a launch feature). Two weeks max. | Answers the wiki's open question: yes, persistence is a prerequisite for the public test. A test on `localStorage` proves nothing and burns the one first impression we get with each community. |
| **D2** | **"concerné(e)s" is final for launch.** "Signer / signatures" is parked until ≥1,000 positive swipes exist, then A/B tested with the Type A/B disclaimer. | The petition vocabulary needs two disclaimers (Type A vs B) and a legal review pass. That is a conversion optimisation, not a cold-start lever. Shipping beats wording. |
| **D3** | **Launch surface = `/communaute/independants`, not the homepage.** One community at a time, one link per community, one curated deck of ~10 cards per community. | Already built. A community-specific link converts better than a generic homepage and gives clean per-community metrics. |
| **D4** | **No paywall, no pricing page before the Cercle 2 signal.** `/devenir-maker` stays "pricing soon" + email capture. The Terminal stays open (no login) so we can observe maker return visits. | An empty paid Terminal kills credibility. Return visits are the metric, not signups. |
| **D5** | **Feature freeze.** Nothing enters Lovable in Phases 2–3 unless it is (a) a bug that blocks voting/opt-in, (b) required by a legal rule, or (c) an instrumentation gap. | Every Lovable message costs an hour of Fabien's week. Distribution costs the same hours and is the actual bottleneck. |
| **D6** | **Seeding is curated, not scraped, for the first 60 cards.** The Make/n8n scraping pipeline (Reddit, X, forums → Claude qualification → moderation queue) is built only in Phase 2 and only feeds a moderation queue, never auto-publishes. | 60 sharp, legally clean, freelance-specific cards beat 500 generic ones. The legal grid (factual lived fact, no value judgment, entity = organisation only) is easier to guarantee by hand at this volume. |

## The 90 days — three phases, one priority each

### Sprint 0 — Audit & freeze (week 1, 11–17 Sep)
**Priority: know exactly what we have, then stop adding.**
- Read the three legal pages once against the `ouch-legal` grid; fix wording only if wrong.
- Export the current catalog (`src/lib/problems.ts`, `src/lib/entities.ts`, `src/lib/voices.ts`) as the seed data for the migration. Review every card against the moderation grid one last time.
- Write the persistence spec (schema, policies, device-id logic, the aggregated view the Score de Douleur reads from) with `ouch-cto` before sending anything to Lovable.
- Set up the metrics sheet (see *Metrics*), even if it starts empty.
- **Exit criterion**: spec written, seed data reviewed, no UI change made this week.

### Phase 1 — Make the votes real (weeks 2–3, 18 Sep – 1 Oct)
**Priority: two different browsers see the same 🔥 counter.**
- Migrate `engagement.tsx` to Supabase for votes, leads, voices, confirmation votes, submitted problems, survey answers. Keep the `localStorage` device id as the anonymous identity.
- Seed the reviewed catalog into `problems`.
- Instrument the 5 events that matter: `swipe_right`, `swipe_left`, `optin_email`, `optin_google`, `problem_submitted`, plus `terminal_visit` with a device id so maker return visits can be counted. A simple `events` table is enough; no analytics SaaS yet.
- Smoke test with 5 friendly freelances on the `/communaute/independants` link. Bugs found here are the only allowed feature work.
- **Exit criterion (hard gate)**: shared counters verified across devices, seed data live, events landing in the table, 5 smoke testers voted without help.

### Phase 2 — First real audience (weeks 4–7, 2 – 29 Oct)
**Priority: 300 distinct freelances have swiped.**
- Build the community deck: 10 curated freelance cards (invoicing, late payment, URSSAF, client ghosting, Malt/platform fees, scope creep, quotes, admin time). Reuse existing cards where they fit; write the rest with `ouch-growth-hacker` + `ouch-persona-victime`, each validated against the legal grid.
- Three distribution waves, one per week, each to a different channel type, each with its own link parameter so channels can be compared:
  1. Fabien's own network (LinkedIn post + direct messages to freelances he knows).
  2. Two or three French freelance communities (Slack/Discord/Facebook groups, Malt/Shine/Indy-type communities — exact list chosen by `ouch-growth-hacker` in week 4). Ask admins first; post as a member, not as a brand.
  3. Reddit / Indie Hackers / X threads where freelances already complain, replying with the specific card, never with the homepage.
- Start the Make scraping pipeline in week 6, feeding a moderation queue (Notion or a Supabase `problem_candidates` table). Publish by hand.
- Publish one entity page (`/entite/:slug`) with a real counter as a share test in week 7. This is the long-planned "public validation test". Observe spontaneous maker reactions; do not reach out to the entity.
- **Exit criterion (hard gate)**: ≥300 distinct voters, ≥10% opt-in (email or Google) on positive swipes, ≥3 cards with ≥50 🔥, ≥10 spontaneously submitted problems. Missing two of the four = extend Phase 2 by two weeks; do **not** start Phase 3 early.

### Phase 3 — First maker signal (weeks 8–12, 30 Oct – 3 Dec)
**Priority: one maker comes back to the Terminal a second time without being asked.**
- Recruit 10 makers by hand (indie hackers, no-code builders, Lovable/Bubble builders, freelance devs looking for a product). Send them the Terminal link and one specific card with real numbers. Track return visits through `terminal_visit` events.
- Run 10 thirty-minute conversations with `ouch-persona-maker`'s questions: would you pay 15–40€/month for this, for what exactly, what is missing to trust the score.
- Keep distribution running at one wave per week (the freelance side must not stall while makers are courted).
- Collect the first pricing signal; write it up with `ouch-cfo`. No billing code.
- **Exit criterion**: the Cercle 2 signal defined in the wiki — 3 freelance problems with Score de Douleur >70 **and** ≥1 maker returning a second time.

### Day 90 decision (week 13, 4–10 Dec)
One of three outcomes, decided in a `panel-ouch-double-face` session:
- **Signal reached** → open Cercle 2 (PME): second community deck, second link, same playbook. Start pricing design.
- **Freelance side works, maker side silent** → the data is valuable but the buyer is wrong; test the alternative buyers (agencies, VC scouts, product studios) before touching pricing.
- **Opt-in rate <5% after two extended phases** → the "validated market" thesis is weak; the honest move is to stop, not to add features.

## Weekly operating rhythm (20h)

| Block | Hours | Phase 0–1 | Phase 2–3 |
|---|---|---|---|
| CEO review (Sunday, 1h) | 1 | Read the metrics sheet, pick the single priority of the week, log the decision in `wiki/log.md` | same |
| Build (Lovable) | 8 → 3 | Persistence migration | Blocking bugs only |
| Distribution & content | 3 → 10 | Prepare decks and copy | Waves, replies, moderation queue |
| Makers | 0 → 4 | — | Outreach, conversations |
| Ops, legal, wiki | 2 | Seed review, legal proofread | Moderation, wiki ingest of learnings |

Rule: if a week ends without a measurable proof (a counter moved, a wave shipped, a maker talked to), the week failed regardless of what was built.

## Metrics

**North Star**: number of *validated problems* = cards with ≥50 🔥 **and** ≥5 opt-ins. This is the unit the maker pays for.

Weekly sheet (one row per week, filled Sunday):

| Metric | Source | Phase 2 target |
|---|---|---|
| Distinct voters | `votes` distinct device id | 300 cumulative |
| Swipes / positive rate | `votes` | positive rate 30–60% (below 30% the deck is off-target, above 60% cards are too generic) |
| Opt-in rate on positive swipes | `leads` ÷ right swipes | ≥10% |
| Problems submitted by visitors | `problems` where source = user | ≥10 |
| Validated problems (North Star) | derived | ≥3 |
| Maker Terminal visits / returning devices | `events` | Phase 3: ≥1 returning |
| Cost per voter by channel | link parameter | qualitative ranking of channels |

## What we are NOT doing before day 90

- AI-suggested business ideas (v2 Pro, needs volume).
- Free entity creation by users; AI entity suggestion queue stays manual.
- New sectors, sub-themes or filters. Segmentation dilutes proof while volume is small.
- Paywall, pricing page, billing.
- Illustrations, gamification extensions, Hall of Fame work, Karma mechanics.
- Any outreach toward a named entity, any "worst company" framing, any public-policy angle.
- Cercle 2 (PME) or Cercle 3 (general public) courting. Content stays broad; *courting* stays freelance-only.
- Homepage redesigns. The homepage is not the launch surface.

## Risks and how they are handled

| Risk | Mitigation |
|---|---|
| Migration eats Phase 2 | Two-week cap. If not shipped by 1 Oct, cut scope to `votes` + `leads` only and ship that. |
| A community admin sees it as spam | Ask first, post as a member, lead with the card not the brand, one post per community. |
| A card names a person or reads as a judgment | Every seeded card passes the legal grid before insert; `qualifyProblem` flags user submissions; moderation queue is manual. |
| Fabien's other commitments compress the week | The Sunday review picks one priority. A 10h week does the priority and nothing else. |
| Makers like the idea but never return | Return visit is the tracked metric from week 8; "liked it" is not a signal. |
| Low positive-swipe rate (<30%) | The deck is wrong for the community, not the product. Rewrite the 10 cards with `ouch-persona-victime`, do not add features. |

## Which skill, when

| Week | Lead skill | Why |
|---|---|---|
| 1 | `ouch-cto` + `ouch-legal` | Persistence spec, legal proofread |
| 2–3 | `ouch-cto` | Migration, instrumentation |
| 4–7 | `ouch-growth-hacker` + `ouch-persona-victime` | Decks, channels, copy |
| 8–12 | `ouch-persona-maker` + `ouch-cfo` | Maker conversations, pricing signal |
| 13 | `panel-ouch-double-face` | Day-90 decision |
| every Sunday | `ouch-ceo` | One priority, one decision, logged |

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Do **not** share `/communaute/independants` externally until Phase 1 ships | now | open |
| Fabien + `ouch-cto` | Write the persistence spec (schema, policies, device id, aggregated view) | 2026-09-17 | **done 2026-09-11** → [`docs/persistence-spec.md`](https://github.com/xeonfab/fix-it-karma/blob/claude/persistence-spec/docs/persistence-spec.md) on branch `claude/persistence-spec` of `xeonfab/fix-it-karma` |
| Fabien + `ouch-legal` | Proofread the three legal pages; final legal pass on the seed catalog | 2026-09-17 | open |
| Fabien | Create the weekly metrics sheet | 2026-09-14 | open |
| Claude Code | Implement the spec from the app repo | 2026-10-01 | **done 2026-09-11** on branch `claude/persistence-spec` (migration applied, 38 cards seeded at zero, client migrated, lint/typecheck/build green) |
| Fabien | Open the PR, merge to `main` (Lovable sync), then run the two-device test on the Lovable preview and the 5-friend smoke test (spec §7 steps 5-6) | 2026-10-01 | open — blocked in the build sandbox (Supabase host not reachable there) |
| Fabien | Phase 1 field check on Vercel, 2026-09-12 00:24–00:40 UTC, one device, `?c=test`: 16 swipes, 7 Google opt-ins, 1 problem submitted through the Claude qualifier, funnel events landing with the channel. Remaining for the gate: the second device (phone) on the same card, then the 5 friendly freelances | 2026-09-14 | open (one device done) |
| Fabien + `ouch-growth-hacker` | Pick the 3 channels and write the 10-card freelance deck | 2026-10-08 | **deck done 2026-09-11** → [freelance deck v1](../projects/2026-09-11_freelance-deck-v1.md) (54 cards, top 10 selected); channel playbook done → [communication plan](2026-09-11_freelance-channel-communication-plan.md); channel map v0 written 2026-09-12 → [freelance channel map](2026-09-12_freelance-channel-map.md), sizes and rules to verify by Fabien |
| Claude Code (`ouch-cto`) | Structure fixes before the first wave: `communities` tag, retire placeholder entities, submission-funnel events, cross-topic dedup | 2026-10-01 | **done 2026-09-11** on branch `claude/freelance-deck-structure` of `xeonfab/fix-it-karma`; migrations applied on the live database (84 cards, 54 tagged, placeholders gone). After the merge with the Lovable exit, `main` validated for real: `npm ci`, `tsc --noEmit` and `npm run build` (Vercel preset) all green; ESLint reports only pre-existing prettier formatting on untouched files |
| Fabien | Merge `claude/freelance-deck-structure` into `main` | 2026-09-14 | **done 2026-09-11** (PR #3), together with PR #2 (Lovable exit: Vite/Vercel, native Supabase auth, Claude API) |
| Fabien | Deploy on Vercel per `docs/deploy.md` (Anthropic key, Google OAuth redirect on the Supabase project, six env vars), then the two-device test on the Vercel URL `/communaute/independants?c=test` and the 5-friend smoke test | 2026-09-14 | open — the Lovable URL still serves the old build on the old database, nothing to share before this |

## Open questions

- Anonymous identity: device id only, or device id upgraded to the Google account when the visitor signs in? (Default: device id, link to `profiles` on sign-in, decided in the spec week.)
- Moderation queue tool: Supabase table read via SQL, or Notion? (Default: Supabase table, one less tool.)
- Which French freelance communities allow member posts about side projects? (`ouch-growth-hacker`, week 4.)

## Related wiki pages

- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- Syntheses: [Community-by-community rollout playbook](2026-09-11_community-rollout-playbook.md) — this plan is iteration #1 of that loop; [Ouch!/FixMyLife — full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Live read of the Lovable project `fix-it-karma` on 2026-09-11: `src/lib/engagement.tsx`, `src/components/ouch/community-survey.tsx`, `roadmap.md`, Supabase table list, message history of 2026-09-10/11
- [raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md](../../../raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 community-rollout-playbook](2026-09-11_community-rollout-playbook.md)
- [2026-09-11 freelance-channel-communication-plan](2026-09-11_freelance-channel-communication-plan.md)
- [2026-09-11 freelance-deck-v1](../projects/2026-09-11_freelance-deck-v1.md)
- [2026-09-11 problem-structure-dedup-spec](../projects/2026-09-11_problem-structure-dedup-spec.md)
- [2026-09-11 team-skills-audit](2026-09-11_team-skills-audit.md)
- [2026-09-12 target-communities-map](2026-09-12_target-communities-map.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
