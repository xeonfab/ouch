---
last_reviewed: 2026-09-13
---

# Channel tracking — links, votes, opt-ins and deposits per `?c=`

> One-line TL;DR: four SQL views on the live `ouch` Supabase project (`channel_funnel`, `channel_weekly`, `channel_problems`, `launch_kpis`) turn the `?c=` parameter of every shared link into a per-channel funnel (visitors → voters → right swipes → opt-ins → problems deposited), read every Sunday into the weekly sheet below and mirrored in French on the Notion page « Com freelances » (section 12). First snapshot 2026-09-13: five channels already live, no deposit event landing (instrumentation gap), two typo'd links.

| Field | Value |
|---|---|
| **Date** | 2026-09-13 |
| **Type** | research (tracking) |
| **Participants** | Fabien, `ouch-data-analyst`, `ouch-cto` |
| **Source(s)** | live schema of Supabase project `ouch` (`mywbvjaitfqclenrvsdn`) read 2026-09-13; [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md) metrics; [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) §7; [channel map v1](../strategy/2026-09-12_freelance-channel-map.md) |

---

## 1. How a link is tracked

- Every shared link carries `?c=<code>` (codes in the [channel map](../strategy/2026-09-12_freelance-channel-map.md)). The client stores it for the session and writes it as `props.utm` on every event (`community_visit`, `swipe_right`, `swipe_left`, `optin_email`, `optin_google`, `vote_retracted`, `entity_page_visit`, `terminal_visit`, the `submit_*` funnel).
- A problem deposited by a visitor carries the same code in `problems.channel`.
- `norm_channel(text)` lowercases, trims and strips anything outside `[a-z0-9-]`, so `amis.` counts as `amis`. A code that is still wrong after that (`fb-fefsi`) stays visible as its own row: fix the link, do not merge by hand.
- Emails are never read by any view; only counts leave the database.

## 2. The views (migration `channel_tracking_views`, applied 2026-09-13)

| View | One row per | Columns |
|---|---|---|
| `channel_funnel` | channel, all time | `visitors` (distinct devices on `community_visit`), `visits`, `voters` (distinct devices that swiped), `right_swipes`, `left_swipes`, `pct_right`, `optins`, `pct_optin_on_right`, `submit_started`, `submit_preview`, `submit_login_wall`, `submit_published`, `problems_deposited` (from `problems.channel`), `first_seen`, `last_seen` |
| `channel_weekly` | channel × ISO week | `visitors`, `voters`, `right_swipes`, `left_swipes`, `optins`, `submit_published` |
| `channel_problems` | problem deposited by a visitor (`source = 'user'`) | `id`, `title`, `statement`, `channel`, `communities`, `published`, `created_at`, `right_count`, `left_count`, `lead_count` |
| `launch_kpis` | one row | `distinct_voters`, `pct_right`, `leads`, `pct_optin_on_right`, `problems_deposited`, `validated_problems` (≥50 🔥 and ≥5 opt-ins), `problems_50_right`, `pct_login_wall`, `computed_at` |

Access: `anon` revoked, `authenticated` and `service_role` can select. Fabien reads them in the Supabase SQL editor or through the Supabase MCP; nothing in the app reads them yet.

```sql
select * from launch_kpis;
select * from channel_funnel order by voters desc;
select * from channel_weekly where week_start >= current_date - 14 order by 1 desc, voters desc;
select id, title, channel, created_at, right_count, lead_count from channel_problems;
-- typo'd codes still in the raw events
select count(*), props->>'utm' from events where props->>'utm' is distinct from norm_channel(props->>'utm') group by 2;
```

## 3. Snapshot — 2026-09-13 12:23 UTC

`launch_kpis`:

| Distinct voters | % right | Leads | % opt-in on right swipes | Deposited | Validated (≥50 🔥 & ≥5 opt-ins) | Cards ≥50 🔥 | Login wall |
|---|---|---|---|---|---|---|---|
| 12 | 61.7 | 14 | 28.0 | 1 | 0 | 0 | no data |

`channel_funnel`:

| Channel | Visitors | Voters | Right | Left | % right | Opt-ins | % opt-in | Deposited | First seen |
|---|---|---|---|---|---|---|---|---|---|
| `fb-fif` (Freelance in France) | 21 | 8 | 12 | 27 | 30.8 | 0 | 0 | 0 | 2026-09-13 |
| `amis` (friends, incl. `amis.`) | 5 | 4 | 31 | 5 | 86.1 | 13 | 41.9 | 0 | 2026-09-12 |
| `fb-cdi` (Cercle des Indépendants) | 2 | 2 | 11 | 0 | 100 | 1 | 9.1 | 0 | 2026-09-13 |
| `fb-cae` (Communauté des Auto-Entrepreneurs) | 2 | 1 | 3 | 0 | 100 | 0 | 0 | 0 | 2026-09-13 |
| `test` | 2 | 1 | 1 | 0 | 100 | 0 | 0 | 1 | 2026-09-13 |
| `fb-fef` (Freelancers En France) | 4 | 0 | 0 | 0 | — | 0 | — | 0 | 2026-09-13 |
| `fb-fefsi` (typo of `fb-fef`) | 1 | 0 | 0 | 0 | — | 0 | — | 0 | 2026-09-13 |

`channel_problems`: one row, id 86 « Un indépendant bloqué 4 jours sur son compte pro, loyer et fournisseur », channel `test`, 2026-09-12, 0 🔥, 0 opt-ins.

Top cards by 🔥 (all under 5 votes, so no ranking yet): 60 jours fin de mois (4), devis refait à la main (4), onze petites modifs (4), arrêt maladie 1 500 € (4), relances impayés (3), commissions plateformes (3).

### Reading (per the data-analyst rules)

- **Everything is "trop tôt"**: 12 voters in total, no channel above 30 voters, no card above 50 votes. No channel ranking this week.
- **The 28 % opt-in is friends**: 13 of the 14 leads come from `amis`. On the Facebook channels the opt-in is 1 on 26 right swipes.
- **`fb-fif` is the first real audience**: 21 visitors, 8 voters, 30.8 % right on 39 swipes, right at the 30 % floor of the plan. If it stays under 30 % after 50 votes, the deck is off for that group, not the product.
- **The gate was not finished before sharing**: the plan's Phase 1 gate (second device, 5 friendly freelances) was still open when the group links went out on 2026-09-13. Not a problem to undo, but the first impression in `fb-fif` is spent.

### Anomalies to fix

| # | Anomaly | Evidence | Owner / fix |
|---|---|---|---|
| 1 | **No deposit event lands.** One problem deposited (id 86) but zero `submit_started`, `submit_preview`, `submit_login_wall`, `submit_published` and zero `problem_submitted` in `events`. The login-wall rate and the deposit funnel are blind. | `select name, count(*) from events group by 1` | `ouch-cto` in `fix-it-karma`: check the four events and `problem_submitted` are emitted client-side with `props.utm`; allowed under D5-c |
| 2 | Two typo'd links: `amis.` (a trailing dot, 2 visitors, 12 opt-ins, merged into `amis` by the view) and `fb-fefSi` (1 visitor, kept as `fb-fefsi`) | `channel_funnel` | Fabien: re-paste the links from the Notion channel table; the old ones keep working |
| 3 | `fb-fef`: 4 visitors, 0 swipes | `channel_funnel` | Check on a phone that the deck loads from that link; otherwise the audience bounced |
| 4 | `pct_login_wall` is null | no `submit_preview` events | same as 1 |

## 4. Weekly sheet (one row per Sunday, filled by the routine or by hand)

| Week ending | Distinct voters | Δ | % right | % opt-in on right | Deposited | Validated | Login wall % | First channel by voters | Verdict |
|---|---|---|---|---|---|---|---|---|---|
| 2026-09-13 | 12 | — | 61.7 | 28.0 | 1 | 0 | n/a | `fb-fif` (8, trop tôt) | Nothing to rank yet. Fix anomaly 1 so that deposits become measurable before the LinkedIn wave. |

Targets (end of Phase 2): 300 distinct voters, 30–60 % right, ≥10 % opt-in, ≥10 deposits, ≥3 validated cards.

## 5. The Sunday routine

A claude.ai Routine « Ouch! — feuille du dimanche (tracking canaux) » is meant to run every Sunday at 18:00 Paris, read the four views, append a row here, refresh the snapshot in Notion section 12 and end with the one-sentence verdict. The routine created from the build session on 2026-09-13 could not carry the Supabase and Notion connectors (organisation setting), so it was deleted; it must be created by Fabien from the claude.ai Routines UI with the Supabase and Notion connectors attached, weekly, Sunday 16:00 UTC, with this prompt:

```
You are running the weekly "feuille du dimanche" for Ouch! / FixMyLife (repo xeonfab/ouch, wiki in wiki/). Act as the ouch-data-analyst skill (read skills/ouch-data-analyst/SKILL.md first). Never invent a number; every figure comes from a query run now.
1. Query the Supabase project "ouch" (id mywbvjaitfqclenrvsdn): select * from launch_kpis; select * from channel_funnel order by voters desc; select * from channel_weekly where week_start >= current_date - 14 order by 1 desc, voters desc; select id, title, channel, created_at, right_count, lead_count from channel_problems order by created_at desc limit 30; select count(*), props->>'utm' from events where props->>'utm' is distinct from norm_channel(props->>'utm') group by 2.
2. In wiki/syntheses/research/channel-tracking.md: append this week's row to "4. Weekly sheet" (distinct voters, delta, % right, % opt-in on right, deposited, validated, login wall %, first channel by voters, one-sentence verdict); replace the tables in "3. Snapshot" with the fresh output and today's timestamp; keep the anomalies table current. Bump last_reviewed. Add a "## [date] metrics | Sunday sheet" entry to wiki/log.md. Commit on branch claude/weekly-tracking and push (git push -u origin claude/weekly-tracking).
3. On the Notion page « Com freelances » (page id 3d91a159db6880bda448e54cfd6b6992), section « 12. Tracking », replace the snapshot table and the "Dernière mise à jour" date, in French. Touch nothing else.
4. End with the verdict in one French sentence: is the Phase 2 gate (300 voters, ≥10 % opt-in, ≥3 cards ≥50 🔥, ≥10 deposits) closer, which single metric to move this week, which channel ranks first by distinct voters. Say "trop tôt" under 30 voters per channel or 50 votes per card. Flag: channels with visits but zero votes, typo'd codes, deposits without submit_published events.
Hard rules: never read or export emails; never invent a number; wiki in English, Notion in French.
```

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Claude Code (`ouch-cto`) | Views `channel_funnel`, `channel_weekly`, `channel_problems`, `launch_kpis` + `norm_channel()` on the live database | 2026-09-13 | **done** |
| Fabien | Create the Sunday routine from the claude.ai Routines UI with the Supabase + Notion connectors (prompt above) | 2026-09-14 | open |
| Fabien + `ouch-cto` | Anomaly 1: make the deposit events land (`submit_*`, `problem_submitted`) in `fix-it-karma` | 2026-09-20 | open |
| Fabien | Re-paste the `fb-fef` and `amis` links without the typo; check `fb-fef` loads on a phone | 2026-09-14 | open |

## Related wiki pages

- Syntheses: [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md) (metrics), [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) §7, [channel map v1](../strategy/2026-09-12_freelance-channel-map.md), [sourcing sheet](sourcing-sheet-entity-cards.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
