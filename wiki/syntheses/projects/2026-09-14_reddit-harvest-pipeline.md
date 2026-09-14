---
last_reviewed: 2026-09-14
---

# Reddit harvest pipeline — complaint in a thread → card proposed → one-click publish and reply

> One-line TL;DR: built 2026-09-14 in `fix-it-karma` ([PR #31](https://github.com/xeonfab/fix-it-karma/pull/31)): a Vercel cron reads the followed subreddits once a day, puts new complaint posts in a private queue, the model rewrites each into a card (or recognises a duplicate of an existing card), and Fabien publishes the card and replies in the thread from `/admin/recolte`, one click each. The cron never publishes and never posts: that is the line between harvesting and spamming, and the plan's D6 rule.

| Field | Value |
|---|---|
| **Date** | 2026-09-14 |
| **Type** | project (build) |
| **Participants** | Fabien, `ouch-growth-hacker`, `ouch-cto`, `ouch-legal` (rules) |
| **Source(s)** | Fabien's request « un process auto pour répondre à des commentaires sur Reddit en créant le problème du post »; live read of `fix-it-karma` (`qualify.functions.ts`, `duplicate.functions.ts`, `entity-registry.server.ts`, `admin/entites.tsx`); [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) §3.4 and §4; [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md) D6 |

---

## What runs by itself, what needs a click

| Step | Who | How |
|---|---|---|
| 1. Read Reddit | cron `/api/recolte/cron`, daily at 07:00 UTC (`vercel.json`; Vercel Hobby refuses anything more frequent and the deploy fails) | Subs read in full: `HARVEST_SUBREDDITS` (default `AutoEntrepreneur,freelance_fr`); generalist subs read by search on freelance vocabulary: `HARVEST_SEARCH_SUBREDDITS` (default `vosfinances,france`). Self posts only, ≥80 characters, ≤10 days, not removed. OAuth « script » account if `REDDIT_*` env vars are set, public JSON otherwise |
| 2. Queue | cron | Table `harvest_candidates` (service role only, RLS, no public policy): raw title and body kept privately, URL, author, status `new` |
| 3. Qualify | cron, ≤8 posts per run | `qualifyStory()` (same prompt and legal rules as a visitor deposit: first person, concrete element, no judgment, entity = organisation or none) then `findDuplicate()` (trigram + LLM judge, threshold 0.7). Result: status `qualified` with a draft, or `duplicate` with the existing card id |
| 4. Decide | **Fabien**, `/admin/recolte` | Pick one of the 2–3 formulations, edit statement and title, **Publier la carte** (row in `problems`, `source = 'harvest'`, `channel = rd-<sub>`, `communities = ['independants']` when the sub is a freelance sub, entity candidate queued if any) or **Écarter** |
| 5. Reply | **Fabien**, one click per thread | Reply text prepared: new card → « Ta galère, je l'ai mise en carte pour compter combien on est… [link ?c=rd-<sub>] … dis “moi aussi” … si la formulation est à côté, dis-le-moi »; duplicate → « Même galère, N personnes déjà dessus : [link] ». **Copier la réponse** (paste by hand) or **Poster dans le fil** (Reddit account configured). **J'ai répondu à la main** closes the loop |

Never done by the pipeline: publishing a card without a click, posting a reply without a click, posting in bulk, republishing a post verbatim, opening a new thread with a link.

## Why not fully automatic

Reddit bans accounts and domains that post the same link across threads without a human behind them, and most French subs forbid self-promotion outright. The plan's rule stands: reply inside an existing complaint thread, with the specific card, as a member. The pipeline removes the reading and writing time (the two hours of the Friday harvest hour) and keeps the two clicks that make the reply a person's reply. Rate to respect: a handful of replies per week per sub, never two in the same thread.

## Code map (`fix-it-karma`)

- `src/lib/harvest-reddit.server.ts` — Reddit read (OAuth or public), filters, queue insert, qualification loop, publish, ignore, reply text, post reply, mark replied
- `src/lib/harvest.functions.ts` — admin server functions (`listHarvestQueue`, `runHarvestNow`, `decideHarvest`, `replyHarvest`), `ADMIN_EMAILS` check
- `src/routes/api/recolte/cron.ts` — cron endpoint (`CRON_SECRET`)
- `src/routes/admin/recolte.tsx` — the queue: to decide, to reply, recently handled
- `src/lib/qualify.server.ts`, `src/lib/duplicate.server.ts` — model calls extracted from the visitor deposit so the harvest shares the exact same rules
- Migrations `problem_source_harvest` (enum value) and `harvest_candidates` (table) applied on the live database 2026-09-14
- `docs/deploy.md` — env vars (`HARVEST_*`, `REDDIT_*`)

## Tracking

Cards published from the queue carry `channel = rd-<sub>` and `source = 'harvest'`; votes coming from the reply link carry `?c=rd-<sub>` in `events`. `channel_funnel` therefore shows, per subreddit, visitors → voters → opt-ins, and `channel_problems` lists the cards. A harvested card that reaches 20 🔥 is a card the deck can use.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Claude Code | Pipeline, queue, admin page, docs | 2026-09-14 | **done**, [PR #31](https://github.com/xeonfab/fix-it-karma/pull/31) to merge |
| Fabien | Set `HARVEST_*` if the default subs are wrong; create a Reddit « script » app and set `REDDIT_*` in Vercel if he wants the « Poster dans le fil » button (otherwise copy and paste) | 2026-09-21 | open |
| Fabien | First run from `/admin/recolte` (« Lancer une récolte maintenant »), read the proposed cards, publish the good ones; verify the subs exist (`r/AutoEntrepreneur`, `r/freelance_fr` were unverifiable from the sandbox) | 2026-09-21 | open |
| Fabien | Reply rhythm: at most 3 replies per week per sub, none before the sub's rules are read | ongoing | open |

## Open questions

- Should harvested cards from generalist subs (`vosfinances`, `france`) be tagged `independants` too? Default no: only the freelance subs feed the deck; the others enrich the catalogue.
- Forums (Free-Work, Grafikart) as a second source: same table (`source = 'forum'`), a scraper per forum. Not before the Reddit loop has produced ten published cards.

## Related wiki pages

- Syntheses: [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) §3.4, §4; [channel map v1](../strategy/2026-09-12_freelance-channel-map.md); [channel tracking](../research/channel-tracking.md); [structure & dedup spec](2026-09-11_problem-structure-dedup-spec.md)
- Concepts: [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 freelance-channel-communication-plan](../strategy/2026-09-11_freelance-channel-communication-plan.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
