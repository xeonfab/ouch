---
last_reviewed: 2026-09-10
---

# Ouch! / FixMyLife — Full project context

> One-line TL;DR: complete context-recovery snapshot of the Ouch!/FixMyLife product — concept, business model, hard product rules, data model, build status, and next steps — as of the last Lovable session.

| Field | Value |
|---|---|
| **Date** | 2026-09-10 |
| **Type** | project |
| **Participants** | Fabien (founder/PM) |
| **Source(s)** | `raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md` |

---

## Context

Fabien runs Ouch!/FixMyLife (Lovable project `fix-it-karma`) as an independent project, with ~20h/week available alongside other professional commitments. This document is a context-recovery dump generated from the full history of product decisions, meant to let Claude resume work on the project without re-litigating settled calls.

## Key points

### Concept
- Two-sided platform: **victims** swipe first-person frustration cards (right = "j'ai ce problème", left = indifference); a positive swipe offers to leave an email to be notified of a solution.
- **Makers** use the "Terminal Maker" dashboard, which ranks problems by **Score de Douleur** = 45% positive-vote volume + 35% conversion rate + 20% opt-in emails collected — a way to find an already-validated market before building anything.

### Business model
- Victim side: free and unlimited swiping — the data volume *is* the product, no monetization there.
- Maker side only: Pro subscription (15–40€/month, solopreneur-calibrated) for detailed demographic data; possible sale of opt-in email lists per problem (would require a consent-copy update — current consent only covers "notify me of a solution", not resale).
- Hard rule: a real entity named on a card *can* become a paying Terminal Maker client like anyone else, but with **no differentiated status and no active outreach** from Ouch! — purely passive/opportunistic channel. No "official entity" account role may ever exist.
- No paywall before the traction signal (see Launch strategy below).
- Reserved for v2 Pro, not built: AI-suggested business ideas inferred from clustering similar problems — judged too risky to show before real data volume (persona Julien: "if the suggested ideas are obvious or generic, I lose confidence instantly"). Teased on `/devenir-maker` only.

### Agent team (Claude skills)
Located in `/mnt/skills/user/`: `ouch-ceo` (Karim, vision/roadmap), `ouch-growth-hacker` (Yasmine, double-sided bootstrapping, scraping/automation, copy), `ouch-cto` (Marc, Lovable/Supabase feasibility), `ouch-ux-designer`, `ouch-cfo`, `ouch-legal`, `ouch-persona-victime` (Léa, freelance graphic designer, Lyon), `ouch-persona-maker` (Julien, skeptical indie dev), `panel-ouch-double-face` (4-round deliberation panel, always anchored on cold-start risk).

### Launch strategy
- Principle: target one population at a time rather than a mainstream launch, to avoid diluting limited work time across multiple content tones.
- **Cercle 1 (current)**: freelances/creators — easy one-sentence framing, strong presence on scrapable channels (Reddit, Indie Hackers, X), fast solo purchase decisions.
- **Signal to move to cercle 2 (PME)**: 3 freelance problems with pain score >70 **and** at least 1 maker returning a second time to the Terminal. No fixed date — traction-gated.
- **Cercle 3 (envisaged)**: general public / citizens (administrative/institutional friction) — already partly present via Lifestyle/Santé/Mobilité sectors and institutional entities (France Travail, URSSAF, CAF).
- Important distinction: the "freelance-first" restriction applies only to **who we actively court as a paying customer** — never to feed content or its viral distribution, which stay broad from day one (institutional/administrative content reaches freelances and the general public alike).

### Positioning — what Ouch! is NOT
- **Twitter/X**: no durable aggregation, no purchase-intent capture. Twitter is a scraping *source* to populate the feed, not a competitor.
- **Trustpilot**: rejected as a model — Ouch! doesn't judge a brand, no public entity replies, no star ratings, no "worst company" ranking.
- **Mention/Mentionlytics/Brandwatch** (social listening, brand-paid): Ouch! inverts the payer (a third party exploits the friction, not the brand fixing it) and adds intent capture (opt-in emails) that social listening never does.
- **Change.org**: closest apparent model (counter, "signature" vocabulary considered) but structurally different — a petition argues and proposes its own solution, asking the named decision-maker to execute it. Ouch! separates: the victim just signals (one short sentence); a third-party maker (not necessarily the entity) invents the solution afterward. Change.org sells pressure on a decision-maker; Ouch! sells a validated market opportunity to a team that will solve it and monetize.
- Persona Julien's summary: *"I've never seen a social-listening tool that hands me '340 people want a solution to THIS exact problem, here are their emails.'"*

### Hard product rules (non-negotiable)
1. An **entité is an organisation only, never a physical person** — a mayor/elected official/identifiable manager can never be tagged as an entity (privacy regime differs from commercial denigration of an org). If the narrative names a person, no entity is tagged even if an org is contextually associated. Enforced in `qualifyProblem`'s system prompt.
2. **No divisive public-policy topics.** Explicitly ruled out any "société"/presidential-election framing (election 18 Apr/2 May 2027). The **civic** angle is valid (document public-service friction) but never a policy stance — only factual *administrative* friction (delays, bugs, opacity) against an institution.
3. Terminology: always **"entité"**, never "organisation", in the visible UI.
4. **No special status for a client entity** — an entity that subscribes to the Terminal is a maker like any other.
5. **No active commercial outreach toward named entities** (explicitly rejected: tweeting a list of problems at a named company to nudge it into creating an account — contradicts the passive channel and reintroduces "name and shame" risk).
6. **No content deletion, ever**, on entity or maker request (legal obligation aside) — problem text and score history stay visible indefinitely. Only emails follow a separate GDPR retention policy with individual right-to-erasure.
7. **No discussion thread / right of reply.** Maker updates and "voix des concernés" are one-way, never a chat.
8. **Always fun/playful tone**, including for institutional/civic topics — never pedagogical or administrative in card writing.

### Legal / moderation grid (`ouch-legal`)
- Central principle: every card stays a **factual, individual lived fact**, never a value judgment on the entity itself.
- Banned words (incl. in verbatims): "malhonnête", "arnaque", "nul", "inacceptable", "vol", "escroquerie" and equivalents. OK: "j'attends mon remboursement depuis 3 semaines"; to fix: "cette entreprise est malhonnête".
- Manual review already applied to 33 catalog cards (4 corrections: Qonto, Malt, Stripe, Impots.gouv).
- Rule now natively built into `qualifyProblem`'s system prompt, with upfront detection (`flagged`/`flagReason`) rather than after-the-fact correction.
- **Type A / Type B** (`resolutionType` field) — see [Resolution Type A/B](../../concepts/Resolution_Type_AB.md).

### "Pétition" vocabulary — nuanced decision
- "Signer"/"signatures" vocabulary was validated in principle for conversion power, conditioned on an honest disclaimer about the real resolution mechanism (third-party maker, not necessarily the entity).
- Later refined by the Type A/B distinction (disclaimer can't be a single one-size-fits-all statement).
- **Actual current app state**: "signer/signatures" was never sent to Lovable — the app still uses "concerné(e)s" and the 🔥 icon. Vocabulary must be settled definitively before any public launch if adopted.

### Data model (as built)
- **Problem**: id, statement (1st person), title (3rd person, must contain a concrete/specific element — frequency, number, precise context, never generic), sector, topic (sub-theme), status, `resolutionType` ("tiers"/"entite"), `topicHashtag` (always generated, context/place/theme, never names an entity), linked entity/entities (optional), vote seeds.
- **Vote**: problemId, direction (right/left), timestamp.
- **Lead**: problemId, email, timestamp (consent = "notify me of a solution" only).
- **Entity**: name, type (Entreprise/Institution publique), sector, description, slug (route `/entite/:slug`).
- **Problem lifecycle statuses**: `Incubation` → `Maker assigné` → `🔍 À confirmer` (new) → `✅ Résolu` (if a majority of original voters confirm, min. 5 responses threshold) or back to `Maker assigné` (if rejected).
- **Sectors**: B2B, Lifestyle, Fintech, Santé, Mobilité — with sub-themes per sector (e.g. B2B → RH/Ventes/Finance/Ops).
- **13-16 named, sourced real entities** so far: SNCF Connect, Doctolib, France Travail, URSSAF Auto-Entrepreneur, Colissimo, Impots.gouv, CAF, Qonto, Malt, Stripe + 3 generic ones (telecom operator, business bank, e-commerce marketplace — deliberately unnamed for lack of solid-enough sourcing).
- **Current storage: client-side `localStorage`** (no real sharing between users) — **Supabase migration identified as the real pending technical chantier**, required before a genuine public launch so votes/scores are credible and shared.

### Build status (last session)
✅ **Done and validated in Lovable**: swipe deck (Framer Motion, sector/sub-theme filtering); Terminal Maker with Score de Douleur, filters, detail panel; `/entite/:slug` pages (light public view / detailed Maker view); AI-assisted problem submission (`qualifyProblem`: free text → reformulation → preview → publish, now proposes 2-3 variants instead of one imposed reformulation, with upfront `flagged`/`flagReason` detection); explicit entity-link confirmation chip (never silent auto-linking); submission screen turned into a large modal with close-confirmation if non-empty; home hub restructured (action banner Swiper/Déposer, global trends, by theme → `/swipe` filtered not `/terminal`, by entity, Hall of Fame moved down); full legal review of the catalog; `topicHashtag` always generated, distinct from entity; "🗣️ Voix des concernés" mini-testimonial (60 chars, keyword-filtered) after a positive swipe; AI illustrations for trending cards (manual/threshold trigger only, flat style, strict no-real-brand-or-logo rule); resolution badges removed from compact home cards, kept only in detail views.

🔄 **Sent to Lovable, status to verify on resume**: "🔍 À confirmer" status + confirmation-vote mechanism by original voters (condition to honestly show "✅ Résolu grâce à vous"); mixing the swipe deck with celebration cards and standout "Voix des concernés" (~1 per 8-10 problem cards) to break the negative-flow monotony; legal pages `/mentions-legales`, `/confidentialite`, `/cgu` (verify completion); retroactive Type A/B qualification of the whole existing catalog.

⏳ **Decided but never sent to Lovable** (verify/relaunch): AI-suggested entity queue (beyond the 13-16 closed ones), manually validated rather than auto-published — bridge to a more open future entity-creation flow.

🚫 **Explicitly ruled out**: free entity creation by any user à la Twitter/@handle (deferred to post-Supabase + traction signal); explicit société/presidential positioning; active entity outreach by public tweet; any physical person tagged as an entity; AI business-idea suggestion feature (deferred to v2 Pro, needs real volume).

### Sitemap (validated)
- Victim register (playful, neo-brutalist): `/`, `/swipe`, `/entite/:slug`, submission via modal.
- Maker register (factual/dark): `/terminal`, `/devenir-maker` (light, "pricing soon" + email capture).
- Legal: `/mentions-legales`, `/confidentialite`, `/cgu`.
- Deferred: "À propos"/SEO blog page, dedicated entity contact page, any real billing system.

### Visual identity and tone
- Neo-brutalist/playful style: yellow, purple, mint green, bold borders, drop shadows (`pop`/`pop-sm`), confetti.
- Two registers never to be mixed: playful/fun for everything victim-facing (institutional topics included), factual/dark only for the Terminal Maker.
- Conciseness rule: cards must be readable in 2 seconds (persona Léa). Titles and statements must contain a concrete, specific element (number, frequency, context), never a generic phrasing.
- AI illustrations (if generated): flat, on-brand, never photorealistic, never a recognizable brand logo/livery.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Verify full completion state of the latest Lovable sends (à-confirmer status, legal pages, deck mixing) | — | open |
| Fabien | Run the long-planned **public validation test**: share `/entite/:slug` links on social and observe spontaneous maker reactions | — | open, never executed |
| Fabien | Definitively settle "signer/signatures" vs "concerné(e)s" vocabulary before any wide public share | — | open |
| Fabien | Decide if/when to build the Supabase migration (real persistence, SSO auth for submission, progressive opening of entity creation) | — | open |

## Open questions

- Is the Supabase migration a prerequisite for the public validation test, or can the test run first on the current `localStorage` prototype?
- Will the "pétition" vocabulary ("signer") be adopted before launch, or is "concerné(e)s" the final choice?

## Related wiki pages

- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- [raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md](../../../raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-10 test-concept-communaute-freelances](../strategy/2026-09-10_test-concept-communaute-freelances.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
