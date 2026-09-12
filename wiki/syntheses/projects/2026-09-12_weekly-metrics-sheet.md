---
last_reviewed: 2026-09-12
---

# Weekly metrics sheet — week 0 (field test)

> One line per week, one figure per metric with its threshold, one verdict. Week 0 is the founder's own field test, not an audience: it validates the instruments, not the product.

| Field | Value |
|---|---|
| **Date** | 2026-09-12 |
| **Type** | project (saved-query) |
| **Owner** | `ouch-data-analyst`, filled every Sunday |
| **Source** | live Supabase project `ouch`, queries in `docs/metrics.sql` of `fix-it-karma` (queries 1–14) |
| **Related** | [90-day launch plan](../strategy/2026-09-11_launch-plan-90-days.md) · [communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) · [dedup spec](2026-09-11_problem-structure-dedup-spec.md) |

## How to read this sheet

- Every figure carries its denominator. Below 50 votes per card or 30 voters per channel the verdict is « too early », no ranking.
- Channels are read from `events.props->>'utm'` (value of `?c=`), never from the referrer.
- Vote sources since 2026-09-12: `swipe` (deck), `card` (home showcase), `list` (community listing and catalogue). Retractions are `vote_retracted` events with `source` and `direction`.
- Emails are counted, never read.

## Week 0 — 2026-09-12 (founder field test, two devices)

> Purged on 2026-09-12 at 02:05 UTC after this line was filled (Fabien's call): all votes, leads and events deleted, card 86 unpublished, card 36 kept canonical. Counters start at zero for the friends wave.

| Metric | Value | Sample | Target (end of Phase 2) | Verdict |
|---|---|---|---|---|
| Distinct voters | 2 | Fabien's Mac + one second device (no user agent recorded, direct) | 300 | instruments only |
| Votes stored | 49 (48 right, 1 left) | after 9 retractions during the retract test | — | — |
| Positive swipe rate | 96 % right | 46 votes in the deck by the Mac, 12 by the second device | 30–60 % | too early, and the founder swipes his own deck |
| Opt-in rate | 7 leads ÷ 48 right swipes = 15 % | 1 distinct email (the founder's) | ≥ 10 % | instruments only |
| Submissions | 1 (card 86, channel `test`) | 3 `submit_started`, 1 `submit_login_wall`, 1 `submit_published` | ≥ 10 | funnel proven end to end |
| Login wall share | 1 wall ÷ 1 preview-or-wall = 100 % | n = 1 | CEO decision if > 50 % | too early |
| Validated problems (≥ 50 🔥 and ≥ 5 opt-ins) | 0 | — | ≥ 3 | — |
| Maker returning on `/terminal` | 0 | no `terminal_visit` event yet | Phase 3: ≥ 1 | — |
| Client errors | 17, one cause | all « Failed to fetch dynamically imported module » at 01:16 UTC, a tab open across the PR #8 deployment | 0 real crashes | fixed by PR #10, no real crash |

### Per channel

| Channel (`?c=`) | Visit devices | Visits | Voters | Right | Left | Right from swipe / card / list | Retracted | Opt-ins | Submissions |
|---|---|---|---|---|---|---|---|---|---|
| `test` | 1 | 16 | 1 | 44 | 2 | 35 / 0 / 9 | 9 | 7 | 1 |
| direct | 1 | 1 | 1 | 12 | 0 | 12 / 0 / 0 | 0 | 0 | 0 |

### Per deck card (10-card launch deck, `deck_rank` 1–10)

Every deck card sits at 1 right / 0 left from the Mac (1, 46, 40, 10, 53, 63) or 0 votes; card 72 (rank 10) has the only left swipe. Ten non-deck freelance cards have 2 right (58, 69, 49, 52, 68, 55, 54, 47, 51, 50). Nothing to rank yet.

### Anomalies flagged before any reading

1. **The second device swiped outside the community deck.** Its 12 right swipes hit cards 41, 58, 49, 47, 55, 54, 52, 51, 69, 68, 50, 42, in id order, at a swipe rhythm (3 s apart), none of the ten curated cards. The community deck code respects the curated ids (`SwipeDeck` sorts by `problemIds`), so the device was on the generic `/swipe` page, reachable from the header and footer of every page including the community one. The generic page serves the whole registry in id order once the topic picker is passed. **Read**: a visitor landing on `/communaute/independants` can leak into a non-ranked, non-freelance deck in one tap. Handed to `ouch-ceo` / `ouch-ux-designer`: on community pages the header « Swiper » should point to the community deck, or the generic `/swipe` should rank by Score de Douleur like the community deck. Until then, deck-card statistics are only meaningful for votes with `source = swipe` on the community page.
2. **Card 86** (the founder's test submission) is a near-duplicate of card 36 (Qonto account blocked for a compliance check): same friction, more specific consequence (4 days, rent and suppliers waiting). It carries an empty `communities` tag (fixed for future submissions by PR #6), the topic « Paiements partagés » (wrong, should be « Budget »), no entity link although the statement names Qonto. Decided 2026-09-12: 36 canonical, 86 unpublished with the purge.
3. **User agent missing** on the second device's events (`props.ua` only exists on `client_error`). Add `ua` and viewport width to `community_visit` so the phone / desktop split is readable; one line in `events.ts`. Not urgent.

### Verdict

The instruments work: channel, source, funnel steps, retractions and client errors all land in `events` with the right keys. There is no audience yet, so no product reading. **The one metric to move next week is distinct voters on `?c=amis`**: five friendly freelances, each swiping the ten deck cards, gives the first honest positive-rate reading (50 votes on the deck).

## Sunday procedure (15 minutes)

1. Run queries 1–4, 7, 9, 10 of `docs/metrics.sql` in the Supabase SQL editor (7-day window), plus 13–14 for vote sources and retractions.
2. Fill one new week block above: the metric table, the per-channel table, the per-card table once a card passes 50 votes.
3. List anomalies first (a counter moving without events, a channel missing, a deck leak), then the verdict in one sentence with the metric to move.
4. Hand duplicates to `ouch-editeur-cartes` (query 11), hashtags naming an entity to `ouch-legal` (query 12).

## Saved queries added this week (`docs/metrics.sql`)

```sql
-- 13. Votes par provenance (semaine) : deck, cartes de l'accueil, liste
select coalesce(props->>'source', 'swipe') as source,
       count(*) filter (where name = 'swipe_right') as right_swipes,
       count(*) filter (where name = 'swipe_left')  as left_swipes,
       count(distinct device_id) as devices
from public.events
where name in ('swipe_right', 'swipe_left') and created_at >= now() - interval '7 days'
group by 1 order by right_swipes desc;

-- 14. Votes retirés (semaine) : taux de fausse manip par provenance
select coalesce(props->>'source', '(inconnue)') as source,
       count(*) as retracted,
       round(100.0 * count(*) / nullif((select count(*) from public.events e2
         where e2.name = 'swipe_right' and e2.props->>'source' = e.props->>'source'
           and e2.created_at >= now() - interval '7 days'), 0), 1) as pct_of_right_swipes
from public.events e
where name = 'vote_retracted' and created_at >= now() - interval '7 days'
group by 1 order by retracted desc;
```
