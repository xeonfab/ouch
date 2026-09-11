---
last_reviewed: 2026-09-11
---

# Ouch! — Community-by-community rollout playbook (founder's strategy)

> One-line TL;DR: Ouch! grows one community at a time — ship, prove problem submission with the freelance community on the channels where it already lives, store and structure what comes in so it can be offered to makers, automate what worked, then replay the loop on the next community. The [90-day launch plan](2026-09-11_launch-plan-90-days.md) is iteration #1 of this loop.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | strategy |
| **Participants** | Fabien (founder, dictated voice note) |
| **Source(s)** | [raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md](../../../raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md) |

---

## Context

Fabien restated the overall strategy in a voice note the same day the 90-day plan was written. The plan is tactical (13 weeks, one priority per phase); this note is the **long-run shape** the plan serves. Nothing here contradicts the plan or its six settled decisions. It adds a framing (a repeatable loop), two emphases (problem *submission* as the tested behaviour; channel multiplicity inside one community) and one new, still-ambiguous element (organisations that *collect* problems).

## Key points

### The loop — one community = one iteration

| Step | What it means | Where it already lives |
|---|---|---|
| 1. Ship | A live product with shared persistence, so two visitors see the same counter | Plan Phase 1 (D1) |
| 2. Pick one community | Cercle 1 = freelances/creators. One community at a time, never a mainstream launch | Plan D3, `/communaute/independants` |
| 3. Map its channels | A community is not one place. Freelances are spread over LinkedIn, Facebook groups, Slack/Discord collectives, forums, Reddit, newsletters. One link parameter per channel so channels can be compared | Plan Phase 2 waves + `?c=` events tag |
| 4. Test problem **submission** | Not only swiping: members must *deposit* their own problems. This is the behaviour the iteration proves | Plan Phase 2 gate (≥10 submitted problems) |
| 5. Store, host, structure | Every problem lands in a shared store and is structured (sector, topic, entity, Type A/B, Score de Douleur) so it can be **offered** to entrepreneurs | Supabase schema, `qualifyProblem`, moderation grid |
| 6. Offer to makers | Terminal Maker, ranked by Score de Douleur | Plan Phase 3 |
| 7. Automate what worked | Progressively, per channel, once a manual wave proved the channel. Automation feeds a moderation queue, never auto-publishes | Plan D6, Make pipeline in week 6 |
| 8. Replay | Second community (Cercle 2 = PME), same playbook, own deck, own link, own channel map | Plan day-90 decision |

### What grows with each iteration

- **Volume of problems** — more communities, more channels, more submissions.
- **Structure** — the more problems, the more sectors/topics/entities are needed to keep them offerable. Structure follows volume; it is not designed upfront (consistent with "no new sectors or filters before day 90").
- **Both sides of the market** — on the supply side, *organisations able to collect problems*; on the demand side, *makers/entrepreneurs able to build a solution*. See the open question below on what "collecting organisations" means.

### Answer to "is the freelance community on several channels?"

Yes. French freelances have no single home; each channel type has a different posting norm and a different automation potential. This is why the plan compares channels with a link parameter rather than picking one.

| Channel type | Role for Ouch! | Posting norm | Automation potential |
|---|---|---|---|
| LinkedIn (personal posts, DMs) | Primary reach for FR freelances; Fabien's own network first | Personal account, card-first, never brand-first | High later: "card of the day" generated from real counters |
| Facebook groups (freelance / auto-entrepreneur / by trade) | Large, mixed audiences; admin-gated | Ask admin, post as a member, one post per group | Low (manual, admin rules) |
| Slack / Discord collectives (freelance collectives, platform communities, tech/no-code communities) | High-trust, smaller, better submission rate expected | Invite-only, ask first, reply in existing threads | Low to medium |
| Reddit / forums (r/freelance-type subs, trade forums) | Reply to existing complaint threads with the specific card; also a scraping *source* | No raw links; value first | Medium: scraping → moderation queue |
| X / Indie Hackers | Scraping source; more useful for the maker side | Reply in threads | Medium: scraping → moderation queue |
| Newsletters / podcasts for freelances | Later, once cards carry real numbers to quote | Pitch one card with data | Low |

The exact list of groups/collectives is picked by `ouch-growth-hacker` in week 4 (already an open item in the plan). Rule carried over: one wave per week, one channel type per wave, ask admins first.

### Automation ladder (progressive, per plan D6)

| Level | What is automated | When |
|---|---|---|
| 0 — Manual | Deck writing, posting, replies, moderation | Phase 2 |
| 1 — Sourcing | Make/n8n scraping (Reddit, X, forums) → Claude qualification → moderation queue. Publish by hand | Week 6 |
| 2 — Distribution content | "Card of the day" per channel, generated from live counters; share links with `?c=` | After ≥3 cards have real volume |
| 3 — Replay kit | Templates for a new community: deck template, channel map, link parameters, metrics row, admin checklist | Before Cercle 2 |

Never at any level: auto-publishing a scraped card, contacting an entity named on a card.

### The replay kit — what each iteration must leave behind

- Community definition (who, what they complain about in one sentence).
- Channel map (table above, filled with actual groups and admin contacts).
- 10-card deck, each card validated against the legal grid.
- Link parameters and the metrics rows for the iteration.
- Learnings logged in `wiki/log.md` (what converted, what got refused by admins, which card wording worked).

## Decisions & next steps

No new decision. The six decisions of the launch plan stand. Additions:

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Clarify "organisations that collect problems" (see open question) before any partner contact | 2026-10-08 | open |
| Fabien + `ouch-growth-hacker` | Fill the channel map with actual freelance groups/collectives and pick 3 for the Phase 2 waves | 2026-10-08 | open (already in the launch plan) |
| Fabien + `ouch-legal` | If relay organisations are pursued: write the rule separating a *relay partner* from an *entity named on cards* | before first partner contact | open |
| Fabien | At day 90, produce the replay kit from the freelance iteration before opening Cercle 2 | 2026-12-10 | open |

## Open questions

- **"Organisations capables de recueillir ces problèmes"** — two readings. (a) *Relay partners*: freelance collectives, coworkings, platforms, federations that gather problems from their members and pass them on — a new supply channel, not in the plan. (b) The product's *entités* named on cards. Reading (a) is the useful one, but it must respect hard rule 5 (no active outreach to entities named on cards): a relay partner must not be an entity that appears on the cards it relays. Default until clarified: reading (a), no partner contact before Phase 2 data exists.
- Submission vs swipe as the tested behaviour: the plan measures both, with swipe as the cheaper first action. Keep swipe as the primary metric and submissions as the second gate, unless Fabien wants submission to be the headline metric.
- Which French freelance communities allow member posts about side projects? (Unchanged from the plan, week 4.)

## Related wiki pages

- Syntheses: [90-day launch plan (CEO)](2026-09-11_launch-plan-90-days.md) — iteration #1 of this loop; [Ouch!/FixMyLife — full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- [raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md](../../../raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 launch-plan-90-days](2026-09-11_launch-plan-90-days.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
