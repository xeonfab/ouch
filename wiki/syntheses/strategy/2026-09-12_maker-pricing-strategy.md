---
last_reviewed: 2026-09-12
---

# Ouch! — Maker pricing strategy: why pay when the problems are public?

> One-line TL;DR: the public space sells the *problem*; the Pro plan sells the *proof and the reach* — opt-in emails, who the concernés are, the trend over time, and the right to send them a one-way update through Ouch!. Public listing stays free by design (it is the maker acquisition funnel); a single Pro plan at 29 €/month (249 €/year) is the hypothesis to test in the Phase 3 maker conversations, not to build before the Cercle 2 signal (D4).

| Field | Value |
|---|---|
| **Date** | 2026-09-12 |
| **Type** | strategy |
| **Participants** | Fabien (founder), `ouch-cfo`, `ouch-persona-maker` (Julien / Nadia), `ouch-ceo` |
| **Source(s)** | [full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md), [90-day launch plan](2026-09-11_launch-plan-90-days.md), [rollout playbook](2026-09-11_community-rollout-playbook.md), `skills/ouch-cfo/SKILL.md`, `skills/ouch-persona-maker/SKILL.md` |

---

## Context

Fabien's question (2026-09-12): *why would a maker pay a subscription when every problem is already visible in the public space? Which prices, which features?*

The premise is correct and intentional. Today the whole surface is open: the catalogue lists cards with their Score de Douleur and raw votes, every `/entite/:slug` page lists its problems, and the Terminal has no login (launch plan D4, kept open to count return visits). The wiki only carried a range (Pro 15–40 €/month, "detailed demographic data") and a parked idea (selling opt-in lists). This page turns that into a free/paid line, a plan structure and the questions that will validate it in Phase 3.

## Key points

### 1. The answer in one line: "voir gratuit, agir payant"

What a maker can *read* stays free. What a maker needs to *decide and act* is paid. The public listing is not a leak of the product; it is the top of the maker funnel (SEO on entity pages, shares of a card with a real counter, the Terminal a friend forwards). Ahrefs, Semrush, Crunchbase, Product Hunt, Google Trends all work this way: the ranking is public, the depth, the history, the export and the alerts are paid.

Julien's test ("what does it save me versus one evening on Reddit?") has one answer Reddit cannot give: Reddit shows him that people complain; Ouch! shows him **how many, who, whether it is growing, and lets him reach the ones who asked to be told of a solution**. None of that is readable from the public card. That is the paid layer.

### 2. Visibility ladder — what is shown where

| Layer | Who sees it | What it shows | Why it is placed there |
|---|---|---|---|
| Public card (swipe, catalogue, entity page) | everyone | statement, title, entity, Type A/B disclaimer, 🔥 count, status, 1 "voix des concernés" | Acquisition on both sides. A card without a counter is a tweet; the counter is the hook. |
| Free Terminal | everyone (no login before the signal; free account after) | ranking by Score de Douleur, filters, 🔥 and opt-in **counts** per card, 7-day trend arrow, card detail panel | Lets a maker verify the ranking is real. Return visits here are the Phase 3 metric. |
| **Pro Maker** | paying makers | everything below in §3 | The intent layer: who, how fast, and reach. |
| Never shown to anyone | — | raw opt-in emails, voter identities, per-device data | Consent covers "be notified of a solution" only. Emails never leave Ouch!. |

Rule: the free Terminal shows the **number** of opt-ins, never their profile. The number proves the score is not invented; the profile is what a maker pays for.

### 3. Pro Maker — the features that justify paying

Ordered by the strength of Julien's "I cannot get this elsewhere":

| # | Feature | What it gives the maker | Depends on |
|---|---|---|---|
| 1 | **Reach the concernés through Ouch!** — send a one-way "maker update" to the opt-ins of a problem the maker has claimed | The only way in France to talk to 47 people who said "warn me when someone fixes this". Emails never exported; Ouch! sends, maker writes. Max 1 update per problem per 30 days. | consent text already covers "être prévenu d'une solution"; hard rule 7 (one-way, no thread) |
| 2 | **Who they are** — opt-in profile per card: statut (micro, EURL/SASU, portage), sector, region, community tag, from `survey_answers` and Google profile | Turns "340 concernés" into "62 % micro-entrepreneurs, 40 % in the creative sector" — the demographic data the founder already planned | `survey_answers`, `communities` tag (built) |
| 3 | **Trend over time** — 30/90-day curve of 🔥 and opt-ins, velocity, date of first vote | "Growing or a one-week spike?" is the question a builder asks before committing weeks | `votes`/`leads` timestamps (built) |
| 4 | **Claim a problem** — set status *Maker assigné*, appear on the card, trigger the *À confirmer* → *Résolu* loop | Public commitment, and the only path to #1 | lifecycle statuses (built) |
| 5 | **Watchlist + weekly alert** — follow cards, entities, topics; email when a card crosses a threshold (50 🔥, 5 opt-ins) | Replaces the manual re-check; the retention mechanic | `events` table (built), one cron |
| 6 | **Full "voix des concernés"** and related cards (same topic, same entity, dedup cluster) | Qualitative colour behind the number; the raw material for the v2 idea clustering | trigram similarity (built) |
| 7 | **Aggregated CSV export** (counts, profile shares, trend, no emails) | Julien wants it in his own spreadsheet | trivial |

Not in Pro, ever: raw email lists, voter identities, a badge or reply right for a named entity (hard rules 4–5–7). Not in Pro v1: AI-suggested business ideas (v2, needs volume).

### 4. Plans and prices — the hypothesis

| Plan | Price | Who | Content |
|---|---|---|---|
| **Free** | 0 € | every visitor, then any maker with a free account | Public cards, entity pages, full ranking, counts, 7-day arrow, 1 claim at a time |
| **Pro Maker** | **29 €/month** or **249 €/year** (≈2 months free) | solopreneurs, indie devs, no-code builders, intrapreneurs paying personally (Nadia) | §3 in full; unlimited claims; maker updates on claimed problems |
| Studio / Team | 79–99 €/month, **deferred** | agencies, product studios, entity teams with several seats | 3–5 seats, shared watchlist, entity-scoped view. Only if the day-90 panel finds agencies/studios as buyers |

Why 29 €:
- Inside the founder's and `ouch-cfo`'s 15–40 € "impulse card" band; below the social-listening floor (Mention-type tools start at 41 €/month, paid by the brand to watch itself).
- The one-sentence justification Julien needs: *"moins qu'une soirée de scraping Reddit, et Reddit ne te donne ni les profils ni le droit de leur écrire."* At a freelance dev's rate, one evening of manual listening costs more than a month of Pro.
- 15 € reads as a toy and leaves no room to cut; 39 € needs the trend and the profile to be dense, which they will not be at activation. `ouch-cfo`'s rule: under-charge and raise, never the reverse.
- Annual at 249 € anchors the monthly price and rewards the makers who return, the same behaviour the traction signal measures.

No free trial: the free tier *is* the trial. No per-problem one-shot pack at launch (adds a second SKU and a second checkout for a 20 h/week operation); revisit only if conversations show makers want one card, not a subscription.

### 5. Unit economics (order of magnitude)

Infra (Vercel, Supabase, Claude API for qualification) is well under 50 €/month at Cercle 1 volumes; the real cost is Fabien's time.

| Pro subscribers | Monthly revenue | Reads as |
|---|---|---|
| 10 | 290 € | infra paid, first proof that the intent layer is worth money |
| 50 | 1 450 € | one paid day per week of Fabien's time |
| 200 | 5 800 € | the project funds its own growth (paid scraping, a freelance moderator) |

Money is not the constraint at any of these lines; the number of *validated problems* (≥50 🔥 and ≥5 opt-ins, the launch plan's North Star) is. A Pro plan over a Terminal with two validated problems sells nothing at any price.

### 6. Timing — unchanged (D4)

Nothing here is built before the Cercle 2 signal (3 freelance problems with Score >70 **and** 1 returning maker). Until then: Terminal open, `/devenir-maker` = "pricing soon" + email capture, no billing code, no locked teaser. What *is* done now is cheap and reversible:

- Keep the data the Pro layer needs landing from day one: `survey_answers`, `communities`, timestamps on `votes`/`leads`, `terminal_visit` events with device id. All already in the persistence spec.
- Never show an opt-in profile or a raw email anywhere public, so the paid layer stays paid later.
- Use the price in the Phase 3 conversations as a hypothesis, not an announcement.

### 7. What to ask the 10 makers in Phase 3 (weeks 8–12)

Ask after they have seen one card with real numbers, in this order, and log the answers in the metrics sheet:

1. "What did you check in the last month to decide what to build next, and how long did it take?" (anchors the alternative)
2. "On this card, what number would you need to see before you spend a week on a prototype?" (validates the North Star threshold)
3. "If you could send one message to the 47 people who opted in, what would it say?" (validates feature #1; if they cannot answer, reach is not the value)
4. Van Westendorp, four prices: at what monthly price is Pro *too cheap to trust*, *a bargain*, *expensive but worth it*, *too expensive*? Expect the acceptable band to straddle 29 €.
5. "Would you rather pay per month, per year, or per problem?" (tests the deferred one-shot pack)
6. For an intrapreneur (Nadia): "Would your company pay for this on a company card, and what would legal ask?" (tests the Studio tier and the no-special-status rule)

Decision rule at day 90: if ≥5 of 10 place 29 € between "bargain" and "expensive but worth it" **and** at least one returning maker exists, open Pro at 29 €. If the band centres under 20 €, the intent layer is not dense enough yet: keep collecting, do not discount.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Adopt the visibility ladder (§2) as the rule for what the public card and the free Terminal show; check the current card detail panel does not expose opt-in profiles | 2026-09-19 | open |
| `ouch-legal` | Confirm that a maker update relayed by Ouch! to opt-ins is covered by the current consent ("être prévenu d'une solution"), and draft the extra consent line needed if makers may also send a *pre-build question* | before Phase 3 (2026-10-30) | open |
| `ouch-persona-maker` + `ouch-cfo` | Run the §7 questions in the 10 Phase 3 conversations; write up the pricing signal | 2026-12-03 | open (planned in the launch plan) |
| `panel-ouch-double-face` | Day-90 decision: open Pro at 29 €, hold, or test other buyers | 2026-12-10 | open |
| `ouch-cto` | Only after the signal: Stripe checkout, `plan` column on `profiles`, Pro-gated queries, maker-update relay job | after day 90 | not started, by design (D4/D5) |

## Open questions

- Does a maker's *pre-build question* to opt-ins fit the current consent, or does it need a second opt-in line at capture time? (`ouch-legal`)
- Should the free Terminal require a free account after the signal (cleaner return-visit tracking, a lead for the Pro upsell) or stay fully anonymous (lower friction)? Default: free account, decided at activation.
- Per-problem one-shot pack (49–99 € for one relay on one card) if makers prefer paying per card: test in question 5, do not build speculatively.
- Studio tier: only if the day-90 panel identifies agencies or studios as real buyers.

## Related wiki pages

- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md) (the ranking stays public; its inputs' detail is the paid layer), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md) (Julien buys Type A cards, Nadia reads Type B)
- Syntheses: [90-day launch plan](2026-09-11_launch-plan-90-days.md) (D4, Phase 3, North Star), [rollout playbook](2026-09-11_community-rollout-playbook.md) (step 6 "offer to makers"), [full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md) (business model, hard rules 4–5–7)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- `skills/ouch-cfo/SKILL.md`, `skills/ouch-persona-maker/SKILL.md`, `skills/ouch-ceo/SKILL.md`
- [raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md](../../../raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md) (business model, social-listening price band 41–249 €/month)

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
