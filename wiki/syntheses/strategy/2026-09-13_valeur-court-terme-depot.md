---
last_reviewed: 2026-09-13
---

# Short-term value of submitting a problem — CEO decision

> One-line TL;DR: Fabien doubted the concept ("people want solutions; submitting a problem gives me nothing back in the short term"). Decision: the concept is not reopened before day 90, but the submission promise is rewritten around the frequent event (other people saying "moi aussi"), a fresh card is guaranteed to circulate for 48 h, and cards carry one factual line on the back. One metric is added to the Phase 2 gate: submitters who come back to see their card within 7 days.

| Field | Value |
|---|---|
| **Date** | 2026-09-13 |
| **Type** | strategy (CEO decision, `ouch-ceo`) |
| **Participants** | Fabien (founder), Karim (`ouch-ceo` skill) |
| **Source(s)** | Fabien's question in session (verbatim below); [launch plan](2026-09-11_launch-plan-90-days.md); [submission flow decision](2026-09-11_depot-probleme-panel-decision.md); [channel plan](2026-09-11_freelance-channel-communication-plan.md) §6; [dedup spec](../projects/2026-09-11_problem-structure-dedup-spec.md) §7 |

---

## Context

Fabien, after testing the submission flow himself on one device (`?c=test`, Phase 1 field check), wrote: « je me pose la question de l'intérêt de ce concept. Est-ce que les gens ne cherchent pas avant tout des solutions à leur problème ? Déposer un problème c'est bien mais j'ai encore aucun retour, et [aucun] élément en échange sur le très court terme pour me faire avancer dans la solution à ce problème. »

No wave has shipped yet and Vercel is not configured, so there is no audience data behind the doubt. The doubt is about the mechanism, not about observed behaviour.

## Key points

### Where the doubt is right

- **The submission reward is deferred and improbable.** Writing, analysing, signing in with Google, then a success screen whose promise is « On te prévient dès qu'un maker s'empare de cette carte ». A maker taking a card is the rarest event in the product; in Phase 2 it will not happen at all. The promise is empty for the first 90 days.
- **Every comparable gives a return within the hour.** Change.org: the signature counter moves. Reddit: replies. Trustpilot: public exposure. Ouch! today: a card with one « concerné·e » and a toast.
- **The strongest immediate reward already built is on the wrong path.** The duplicate screen (« Quelqu'un a déjà signalé ça 👀 », N concerné·es, douleur /100) is the one moment where a submitter sees proof that they are not alone, and it appears only when the card already exists.
- **The wiki's stock answer to « C'est quoi l'intérêt pour moi ? » is weak**: « voir que t'es pas seul, et être prévenu si quelqu'un construit une solution » (channel plan §6). The second half is the improbable event again.

### Where the doubt is wrong

- **Nobody comes to Ouch! for a solution, and they must not.** For a solution a freelance has Google, ChatGPT, the accountant and the Facebook group. A pivot to « on te donne la réponse » makes Ouch! one more forum, with the same cold start, competing with ChatGPT, and without the maker thesis (the Terminal needs problems, not answers).
- **The victim-side thesis is « ma galère compte », not « je dépose et je reçois ».** It is the petition mechanic: the return is the counter and the social proof, not the resolution. Petitions work with zero short-term solution, on one condition: the counter moves fast and visibly.
- **The concept does not rest on spontaneous submissions.** D6 seeds 54 curated cards; swipes are the volume. Spontaneous submissions are one of the four Phase 2 exit criteria (≥10). If that criterion fails, the plan learns something; the concept does not fall.
- **The two sides are not the same act.** The swipe is cheap and already rewarding (a quiz-like « ça m'arrive » plus « t'es pas seul »); the submission is expensive. The fix targets the submission, not the concept.

### Decision (Karim, `ouch-ceo`)

1. **The concept is not reopened before the day-90 decision.** The question « do people submit when the return is a moving counter rather than a solution? » becomes an explicit Phase 2 hypothesis, measured, not debated.
2. **Three changes, cheapest first**, so that the hypothesis is testable at all. Without them the criterion « ≥10 spontaneous submissions » measures a broken promise, not the appetite to submit.

| # | Change | Cost | Hard-rule check |
|---|---|---|---|
| 1 | **Promise the frequent event, not the rare one.** Success screen and lead email: « on te dit quand d'autres freelances disent "moi aussi" », email at 5, 10, 25 concerné·es. The maker event stays a second, secondary line. | copy + one trigger on `votes` | one-way notification, no thread (rule 7) ✔ |
| 2 | **Guaranteed circulation for 48 h.** A card submitted with 0 votes gets one slot in the community swipe deck for 48 h so its counter moves the same day. Already specified in [dedup spec §7](../projects/2026-09-11_problem-structure-dedup-spec.md#7-presentation-rules); verify whether it shipped with `deck_rank`, build it if not. | small code | ✔ |
| 3 | **One factual line on the back of each card.** The mechanism fact that helps (« les pénalités de retard et l'indemnité forfaitaire de recouvrement sont des mentions obligatoires, rarement réclamées »), never a threshold or an amount that changes yearly, sourced in the [sourcing sheet](../research/sourcing-sheet-entity-cards.md), from the [expert review](../projects/2026-09-11_freelance-deck-v1_expert-review.md). Not a solution, the fact that unblocks. Applies to swiped cards too. | content, no code (the card back already exists) | `ouch-legal` pass: factual information, never personalised advice; fun register kept ✔ |

3. **Changes 1 and 2 are exceptions to the feature freeze (D5)**, granted on ground (c) « instrumentation gap »: they are what makes the submission hypothesis measurable. Nothing else enters the freeze on this basis.
4. **One metric added to the weekly sheet and to the Phase 2 gate**: *submitters who come back to see their card within 7 days* (device id of `problem_submitted` seen again on the card or the community page within 7 days). Target for Phase 2: ≥50 % of submitters. Below 30 %, the submission promise is still wrong; the concept question reopens at day 90 with that number, not before.
5. **Channel plan §6 answer rewritten**: « Voir en 48 h combien de freelances ont exactement la même galère que toi. Et si un jour quelqu'un construit une solution, t'es prévenu·e en premier. »

### What is explicitly not done

- No « solutions » section, no tips, no replies, no threads under a card (rule 7, and it is the forum pivot).
- No AI-generated « voici ce que tu peux faire » after submission: personalised advice, legal exposure, and it competes with the maker.
- No change to the swipe side beyond the card back.

## Tickets for `xeonfab/fix-it-karma` (ready to paste)

The app repository could not be attached to the session that wrote this page; the three tickets below are written to be pasted as GitHub issues, labels `phase-2`, `d5-exception`. Replace the relative wiki links by their GitHub URL in `xeonfab/ouch` when pasting.

### Ticket 1 — Submission promise: notify on « moi aussi » milestones, not only on maker pickup

**Why.** The success screen promises « On te prévient dès qu'un maker s'empare de cette carte ». That event will not occur in Phase 2. Submitters get nothing back. Decision: this page.

**Scope.**
- `submit-flow.tsx`, `step = "published"`, both modes: primary line becomes « On te dit dès que d'autres freelances disent "moi aussi" 🔥 », secondary line « …et en premier si un maker s'en empare ». Same for the « Connecte-toi pour être prévenu·e » block.
- Milestone notification: when a card's positive votes cross 5, 10 and 25, one email to the leads of that card (submitter and « moi aussi » opt-ins). Idempotent per (lead, card, milestone). Implementation: a `vote_milestones` table (`problem_id`, `milestone`, `sent_at`) plus a scheduled function or a trigger on `votes`; email through the provider already configured for the lead notification (check `docs/deploy.md`).
- Copy, fun register: « 10 freelances ont dit "moi aussi" sur ta carte 🔥 » + link to the card. No reply address, no thread.
- Consent: the existing lead consent is « être prévenu d'une solution ». `ouch-legal` to confirm that a vote-milestone email fits, or extend the consent copy at opt-in before shipping.
- Event: `milestone_email_sent` with `problem_id`, `milestone`.

**Done when.** Two devices vote on a fresh card until 5; the submitter receives exactly one email; the success screen shows the new promise on both modes.

### Ticket 2 — Fresh card guaranteed in the community swipe for 48 h

**Why.** A submitted card ranked by Score de Douleur starts last and is never swiped, so its counter never moves. Specified in the dedup spec §7 (« one guaranteed slot in the swipe for 48 hours »); confirm whether `deck_rank` covers it.

**Scope.**
- `/communaute/:slug` deck query: the top-10 by Score de Douleur, then replace the last slot(s) with cards tagged for this community, `created_at` within 48 h, not merged, not `verifying`/`resolved`, oldest first, at most 2 fresh cards per deck.
- Position in the deck: slot 3 to 5, not first (the first card sets the tone and must be a proven one).
- Frozen order rule (PR #8) unchanged: computed once per page load.
- Event: `swipe_right`/`swipe_left` already carry `problem_id`; add `fresh: true` in props when the card came through the guaranteed slot, so the weekly sheet can read the fresh-card vote rate.

**Done when.** A card submitted from device A appears in device B's deck within one page load, at slot 3–5; after 48 h it is ranked normally.

### Ticket 3 — One factual line on the card back (« Le saviez-vous »)

**Why.** The only short-term « something in exchange » compatible with the positioning: not the solution, the fact that unblocks. Applies to swiped and submitted cards.

**Scope.**
- Content, not code: a new nullable column `fact_line` (≤ 140 chars) on `problems`, shown on the card back under the title, prefixed « 💡 », fun register.
- Source: the [expert review](../projects/2026-09-11_freelance-deck-v1_expert-review.md) mechanism column. Rules: a mechanism, never a threshold, an amount or a date that changes yearly; no personalised advice; one public source per line logged in the [sourcing sheet](../research/sourcing-sheet-entity-cards.md); `ouch-legal` pass before insert.
- First batch: the 10 launch-deck cards, written by `ouch-expert-independants`, edited by `ouch-editeur-cartes`, inserted by SQL migration.
- User-submitted cards: `fact_line` stays null; it is written by hand at the Sunday moderation pass, never generated by `qualifyProblem`.

**Done when.** The 10 launch cards show their line on the back on mobile; a card without a line shows nothing (no empty prefix).

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Paste the three tickets in `xeonfab/fix-it-karma` (or attach the repo to a Claude Code session so they are opened from here) | 2026-09-14 | open |
| Fabien + `ouch-legal` | Confirm the lead consent covers vote-milestone emails, or extend the opt-in copy | before ticket 1 ships | open |
| `ouch-expert-independants` + `ouch-editeur-cartes` | Write the 10 fact lines for the launch deck, log sources | 2026-09-21 | open |
| Claude Code (`ouch-cto`) | Tickets 1 and 2 on a branch of the app repo, validated locally, two-device test | before wave 1 | open |
| Fabien | Add « submitters back within 7 days » to the weekly sheet | 2026-09-14 | open |

## Open questions

- Milestone thresholds 5 / 10 / 25 are a guess; adjust once the fresh-card vote rate is known (ticket 2 event).
- Should the fact line be generated for user-submitted cards later (Phase 3, with a legal filter), or stay hand-written for good?

## Related wiki pages

- Syntheses: [90-day launch plan](2026-09-11_launch-plan-90-days.md) (D5, D6, Phase 2 gate, metrics), [Dépôt d'un problème — décision du panel](2026-09-11_depot-probleme-panel-decision.md) (success screen), [Freelance channel communication plan](2026-09-11_freelance-channel-communication-plan.md) (§6 objection), [Problem structure & dedup spec](../projects/2026-09-11_problem-structure-dedup-spec.md) (§7 48 h slot), [Freelance deck v1 — expert review](../projects/2026-09-11_freelance-deck-v1_expert-review.md), [Sourcing sheet](../research/sourcing-sheet-entity-cards.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Fabien's question in the Claude Code session of 2026-09-13 (no raw file; quoted in Context)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 freelance-channel-communication-plan](2026-09-11_freelance-channel-communication-plan.md)
- [2026-09-11 launch-plan-90-days](2026-09-11_launch-plan-90-days.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
