---
last_reviewed: 2026-09-13
---

# Freelance channel communication plan — collect problems, convince freelances to submit

> One-line TL;DR: one funnel (see a card → swipe → opt-in → submit your own), one register (fun, first person, never brand-first), one playbook per channel type with ready-to-paste French copy, a weekly harvest protocol that turns what freelances already complain about into cards, and one rule settled by Fabien on 2026-09-12: every message sends people to the page with **two verbs, vote on what exists and deposit what is missing**; proxy submission (we write the card from a complaint) is only the fallback for someone who describes their problem in a comment instead of depositing it.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | strategy |
| **Participants** | Fabien (founder), `ouch-growth-hacker` (Yasmine), `ouch-persona-victime` (Léa), `ouch-legal` |
| **Source(s)** | [rollout playbook](2026-09-11_community-rollout-playbook.md), [90-day plan](2026-09-11_launch-plan-90-days.md) Phase 2, live read of `submit-flow.tsx` and `communaute.independants.index.tsx` (2026-09-11) |

---

## Context

Workstream 2 of the freelance push. The plan already fixes the frame: launch surface `/communaute/independants`, three weekly waves, one channel type per wave, one `?c=` parameter per channel, ask admins first, post as a member. This page makes it executable: what to say, where, how often, and how a complaint found on a channel becomes a card. Nothing here starts before the Phase 1 gate (shared counters verified). Until then, the only outside contact is the 5-friend smoke test.

## 1. The funnel and where it leaks

| Step | Action asked | Cost for the freelance | Current state | Leak to watch |
|---|---|---|---|---|
| 1 | Open the community link | one tap | built | channel mismatch (wrong audience) |
| 2 | Swipe 10 cards | 20 seconds, no account | built (D1: no login to swipe) | positive rate <30 % = wrong deck |
| 3 | Leave an email / Google sign-in after a right swipe | 5 seconds | built | opt-in rate <10 % |
| 4 | **Submit their own problem** | write 2 sentences + **Google login to publish** | built, login required (`problems_insert_authenticated`) | the login wall, unmeasured today |
| 5 | Share the card | one tap | built (native share / X intent) | none |

The login wall at step 4 is the single biggest unknown for "convaincre de déposer". Three responses, in order (revised 2026-09-12: Fabien's feedback on the first draft was that it leaned on him writing cards from comments, which makes him the bottleneck and never installs the reflex « je vais sur la page, je vote, je dépose »):
1. **Ask for the deposit directly, in every message.** The destination is the page, with two verbs: vote on the cards that exist, deposit the one that is missing. Google sign-in is one tap for most people; we do not route around the wall before it is measured.
2. **Measure it** (the four events `submit_started`, `submit_preview`, `submit_login_wall`, `submit_published` shipped 2026-09-11): if more than half of the people who reach the preview stop at the wall, escalate to the CEO for a decision on anonymous publication (device id + moderation queue). Not before the numbers exist.
3. **Proxy submission as the fallback only** (section 4): when someone describes their problem in a comment or a thread instead of depositing it, the first reply sends them to the page. If they have not deposited after 48 h, Fabien writes the card and sends them the link to vote on it. Their problem lands in the registry either way, but the default path is theirs. If fallback cards outnumber direct deposits, the messages are not pushing hard enough toward the page.

## 2. Register and message (victim side, fun)

- **One-line positioning for freelances**: « Tes galères de freelance, enfin utiles. » Variants: « Swipe tes galères, on les met sous le nez de gens qui construisent des solutions. » / « Ici, râler sert à quelque chose. »
- **Always card-first, never brand-first.** A post opens with a card statement, in quotes, first person. The name Ouch! appears at the end or not at all.
- **The ask is never « inscris-toi ». It is always two verbs, at the destination**: « vote celles que tu vis » (swipe, 20 seconds, no account) and « la tienne n'y est pas ? dépose-la en deux phrases, elle devient une carte que les autres votent » (submit, Google login). Every message ends on both. « Dis-le-moi en commentaire, je l'ajoute » is no longer the hook: a comment is a fallback we redirect to the page. Why the page and not the comment, when asked: « un commentaire disparaît dans le fil ; une carte a un compteur, les autres votent dessus, et tu es prévenu si quelqu'un s'en empare ».
- **Numbers only when real.** Before counters exist, the hook is recognition (« lequel de ces 10 te parle ? »). Once a card passes 20 🔥, the hook becomes the number (« 47 freelances ont la même galère que toi »).
- **Never**: naming an entity in the hook, a « pire boîte » angle, a policy stance, a promise that the problem will be solved. What we promise: « tu seras prévenu si quelqu'un s'en empare ».

Léa's filter on every piece of copy: would she tweet it herself, in those words? If it sounds like a startup, rewrite.

## 3. Channel playbook

Each channel gets its own link `https://…/communaute/independants?c=<canal>` so the Sunday metrics compare channels. Suggested values: `li` (LinkedIn post), `dm` (direct messages), `fb-<groupe>`, `sl-<collectif>`, `rd` (Reddit), `fo-<forum>`, `nl` (newsletter).

### 3.1 LinkedIn, personal account — wave 1 (week 4)

- **Goal**: 100 distinct voters from Fabien's own network; first 10 problems deposited by their own authors.
- **Format**: one post per week + 20 DMs per week. Post as a freelance-adjacent founder telling a story, not as a product launch.
- **Cadence**: post Tuesday morning, DMs spread Tuesday to Thursday, reply to every comment within the day.
- **Post template (week 4)**:

  > « Chaque vendredi, je perds trois heures à relancer mes factures impayées. »
  > « Onze “petites modifs” gratuites, soit deux jours non facturés. »
  > « Une semaine d'arrêt maladie : 90 € d'indemnités, 1 500 € de facturation perdue. »
  >
  > J'ai listé les galères de freelances que j'entends en boucle, et on compte combien on est sur chacune.
  > 👉 [lien]
  >
  > Deux choses à faire là-bas, pas plus :
  > 1. Swipe les galères : à droite si tu la vis. 20 secondes, pas de compte.
  > 2. La tienne n'y est pas ? Dépose-la en deux phrases. Elle devient une carte, et ce sont les autres freelances qui votent dessus.
  >
  > Le but : que ceux qui construisent des solutions voient enfin combien on est sur chaque galère, chiffres à l'appui.

  Someone who tells their problem in a comment instead of depositing it gets the redirect reply of section 3.7. Reply to every comment within the day.
- **DM template**: « Salut [prénom], je bosse sur un truc pour les freelances : on recense nos galères concrètes (impayés, TVA, devis, plateformes…) et on compte combien on est sur chacune, pour les mettre sous le nez de gens qui construisent des solutions. Deux minutes : swipe celles que tu vis 👉 [lien], et si ta pire galère n'y est pas, dépose-la directement là-bas en deux phrases, elle aura son compteur. Tu me dis ce que t'en penses, même si c'est “aucun intérêt” ? »
- **Do not**: tag companies, use the word « plateforme » in the hook, post the homepage.

### 3.2 Facebook groups (freelances, auto-entrepreneurs, by trade) — wave 2 (week 5)

- **Goal**: 100 voters from two or three groups; find the first 10 complaints to harvest.
- **Selection** (`ouch-growth-hacker`, week 4): groups with >5 000 members, active daily, rules that allow member projects or at least questions. Exact names to be picked and logged in the channel map; French groups around « freelance », « auto-entrepreneur / micro-entrepreneur », « graphistes / développeurs / rédacteurs freelance » are the pool.
- **Admin message first** (mandatory): « Bonjour, je suis membre du groupe et je travaille sur un projet perso, sans but commercial à ce stade : recenser les galères concrètes des freelances pour qu'elles arrivent aux bonnes personnes. Est-ce que je peux poster une fois un lien vers un test de 20 secondes (pas de compte, pas de pub) ? Je respecte évidemment votre réponse. »
- **Post template**: opens with a *question*, then sends to the page with both verbs: « Question sérieuse : c'est quoi la galère de freelance que vous n'arrivez pas à régler depuis des mois ? J'ai commencé à les recenser ici, avec un compteur pour chacune 👉 [lien]. Si la vôtre y est, votez-la (20 secondes, pas de compte). Si elle n'y est pas, déposez-la là-bas en deux phrases : elle devient une carte que les autres peuvent voter. Ça sert à une chose précise : compter combien on est sur chaque galère, pour que quelqu'un s'en empare. » If the group forbids links in the post body, the link goes in the first comment and the post says so. Replies that describe a problem instead of depositing it get the section 3.7 redirect.
- **Rule**: one post per group, ever. Then only replies inside other people's threads.

### 3.3 Slack / Discord collectives — wave 2 (week 5–6)

- **Goal**: the best submission rate; these members already talk about their problems in `#entraide`-type channels.
- **Approach**: join as a member two weeks before posting, answer three questions from others first, then ask in the relevant channel: « Je recense les galères de freelances avec un compteur pour chacune (impayés, TVA, devis, plateformes…). Si vous avez deux minutes : votez celles que vous vivez, et déposez celle qui manque, elle devient une carte. Lien en fil. Retour franc bienvenu, même “aucun intérêt”. » Send the community link in thread, never in the channel body.
- **Harvest**: pinned complaints and recurring threads are the richest source of cards; rewrite, never quote.

### 3.4 Reddit and forums — wave 3 (week 6)

- **Goal**: harvest first, votes second. French subs and forums for auto-entrepreneurs and freelances; exact list to verify (many ban self-promotion outright).
- **Rule**: never post a raw link as a new thread. Reply inside an existing complaint thread with the *specific card* and its real counter once it exists: « Même galère listée ici, 32 freelances dessus 👉 [lien carte]. Vote-la si c'est la tienne. Et si tu en as une autre en tête, dépose-la là-bas, elle aura son compteur aussi. » Before counters exist, do not post at all; just harvest.
- **Harvest**: one hour per week reading the newest complaint threads; each one that passes the standard becomes a card (section 4).
- **Automated since 2026-09-14**: the [Reddit harvest pipeline](../projects/2026-09-14_reddit-harvest-pipeline.md) does the reading and the rewriting every six hours; Fabien keeps the two clicks (publish the card, reply in the thread) on `/admin/recolte`.

### 3.5 X / Indie Hackers — continuous, low effort

- Scraping source for the Make pipeline (week 6+) and maker-side channel later. Card-of-the-day posts start only when three cards have real numbers.

### 3.6 Newsletters and podcasts for freelances — after week 8

- Pitch one card with a real number to two or three French freelance newsletters. Not before the deck has data worth quoting.

### 3.6 bis Card-first post with a visual (Facebook, LinkedIn) — added 2026-09-13

Fabien's variant, preferred for the Facebook feed: the post shows **one card** as an image (1080×1350, template `tools/card-visual/` in the `ouch` repo), the text opens with the card's sentence, the two verbs follow, the link goes in the first comment. The link carries `?c=<canal>&p=<id>` so the swipe opens on the card shown (`?p=` shipped 2026-09-13 on `fix-it-karma`, [PR #26](https://github.com/xeonfab/fix-it-karma/pull/26); without it the deck is ordered by pain score and the shown card is rarely first). One post per group still; further cards only in replies or, with the admin's consent, one every two weeks. French copy on the Notion page, section 5.4 bis.

Persona pass 2026-09-14 (`ouch-persona-victime` Léa, `ouch-persona-maker` Julien): Léa swipes the card but finds the post too long and « elle devient une carte » meaningless; Julien discounts any number driven by the `amis` channel and wants the validation threshold visible. Applied the same day: the post is cut to three lines (sentence, the two verbs, « lien en premier commentaire »), the visual says « les autres freelances diront “moi aussi” » instead of « elle devient une carte », and the share loop in the app carries the two verbs (see 3.6 ter).

### 3.6 ter The share loop, as built (2026-09-14)

A deposited card has its own page `/probleme/<id>` with an Open Graph image, a « Moi aussi » button and share links; the success screen shares `/probleme/<id>?c=share`. Added in [PR #30](https://github.com/xeonfab/fix-it-karma/pull/30) of `fix-it-karma`: the shared text asks for both gestures (« moi aussi » in 20 seconds without an account, « dépose la tienne »), the card page offers « Déposer ma galère » (opens the submission modal with the card's community) and, for freelance cards, links to the community deck instead of the generic swipe. The croisière criterion reads on `channel_funnel`: visitors with channel `share` versus Fabien's own codes.

### 3.7 When someone tells their problem in a comment instead of depositing it

First reply, always, the redirect: « Ça mérite une carte. Dépose-la directement ici en deux phrases 👉 [lien] : c'est toi qui dois être compté dessus, pas moi. Et les autres pourront dire “moi aussi”. »

Fallback, only if nothing has been deposited 48 h later: Fabien writes the card from the comment (section 4 standard), then: « Je l'ai ajoutée pour toi : “[phrase de la carte]”. C'est bien ta galère ? Si oui, swipe à droite ici 👉 [lien carte], ça te compte dessus et tu seras prévenu si quelqu'un s'en empare. »

## 4. Harvest protocol — from channel complaint to card (1 h per week, Fridays)

1. **Collect**: read the week's threads on the chosen channels; copy the complaint, the URL, the date and the channel into the sourcing sheet (private).
2. **Rewrite** to the card standard (never verbatim, legal rule): one first-person sentence with the concrete element, a third-person title, sector/topic, hashtag without entity, entity only if real and clearly named, Type A/B. The `qualifyProblem` function can produce the first draft: paste the complaint as the story.
3. **Dedup** against the registry (spec query); if it matches an existing card, do not create one, note the URL as extra evidence for that card.
4. **Legal grid**: banned words, no person, no generalisation. Entity-named card → source logged (already done in step 1).
5. **Insert** as `source = 'seed'`, counters at zero, tagged with the community.
6. **Close the loop with the author** when reachable, with the fallback message of section 3.7. One right swipe from them validates the card and often brings an opt-in.

Harvest is for complaints already published elsewhere (forums, Services Publics+, old threads). People who answer Fabien directly are sent to deposit themselves first (section 3.7). Target: 10 harvested cards per week in Phase 2, on top of the 54 seeded ones. The Make pipeline in week 6 automates step 1 only; steps 2–6 stay manual until day 90 (D6).

## 5. Converting swipes into submissions on the page itself

Three levers, all copy or instrumentation, none a new feature:

- **End-of-deck slot**: the existing `CommunitySurvey` asks « ça sonne vrai ? » and « qu'est-ce qui manque ? ». Its `missing` field is already a submission in disguise: every answer is read on Sunday and turned into a card by hand, then the answer's device is targeted with the card in the next wave. Copy to tighten: « Ta galère n'y est pas ? Écris-la ici en une phrase, on en fait une carte. »
- **The block above the deck** (« Ton problème n'y est pas ? Ajoute-le 💣 ») moves *below* the deck: nobody submits before swiping; after ten cards they know what a card looks like.
- **After publishing**: the share prompt already exists. Add the community link to the share text so a shared card lands on the freelance deck, not the homepage.

## 6. Objections and answers (for DMs and comments)

| Objection | Answer |
|---|---|
| « C'est quoi l'intérêt pour moi ? » | « Voir que t'es pas seul, et être prévenu si quelqu'un construit une solution. C'est tout, et c'est gratuit. » |
| « Pourquoi je dois aller là-bas, je te le dis ici » | « Un commentaire, ça disparaît dans le fil. Une carte, ça a un compteur, les autres votent dessus, et tu es prévenu si quelqu'un s'en empare. » |
| « Il faut un compte ? » | « Pas pour voter. Pour déposer, oui, connexion Google en un clic : c'est ce qui garantit qu'une carte vient d'une vraie personne, et ça permet de te prévenir. » |
| « Vous faites quoi de mon email ? » | « Uniquement te prévenir si une solution sort pour cette galère précise. Rien d'autre, c'est écrit au moment où tu le laisses. » |
| « Encore une plateforme… » | « Pas de compte pour swiper. 20 secondes. » |
| « Ça sert à rien de râler » | « Ici ça sert à un truc précis : compter combien de freelances ont exactement la même galère, pour que quelqu'un la prenne au sérieux. » |
| « Vous allez balancer des boîtes ? » | « Non. On décrit des faits vécus, jamais un jugement sur une boîte. Une entreprise nommée peut d'ailleurs venir lire ce qui remonte, comme n'importe qui. » |

## 7. Weekly rhythm and metrics (Phase 2, 10 h/week on distribution)

| Day | Block | Hours |
|---|---|---|
| Sunday | CEO review: metrics by `?c=`, pick the week's channel and card | 1 |
| Tuesday | Post + DMs (LinkedIn) or group post (wave 2) | 3 |
| Wed–Thu | Replies, thread participation, redirects to the page (3.7) | 3 |
| Friday | Harvest hour + card writing + insertion | 2 |
| Any | Moderation of user submissions and survey answers | 1 |

| Metric (per channel, from `events.props.utm`) | Target by end of Phase 2 |
|---|---|
| Distinct voters | 300 cumulative |
| Positive swipe rate | 30–60 % |
| Opt-in rate on right swipes | ≥10 % |
| **Problems deposited by visitors themselves** (`source = 'user'`) | **≥10** — headline metric with distinct voters |
| Harvested cards inserted (public complaints rewritten) | ≥30 |
| Fallback cards (written from a comment) then voted by their author | tracked, no target; if it exceeds direct deposits, the messages are not pushing to the page enough |
| Reached preview → stopped at login wall | measured, decision if >50 % |

## 8. Legal and community guardrails (non-negotiable)

- No outreach to an entity named on a card, ever; no tagging companies in posts.
- No « pire entreprise », no ranking of brands, no policy angle; civic friction stays factual and administrative.
- Every harvested card is rewritten; verbatim republication of someone's post is forbidden.
- Ask group admins before posting; one post per group; leave when asked.
- The consent copy on opt-in stays « être prévenu d'une solution »; no reuse of emails for outreach.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Claude Code (`ouch-cto`) | Add the four submission-funnel events (allowed under D5-c) | 2026-10-01 | open |
| Fabien + `ouch-growth-hacker` | Fill the channel map: 3 Facebook groups, 2 Slack/Discord collectives, 2 forums/subs, with admin contacts and `?c=` values | 2026-10-08 | open |
| Fabien | Create the private sourcing sheet (URL, date, channel, card ref) | 2026-10-01 | open |
| Fabien | Wave 1 LinkedIn post + 20 DMs with the template above | week of 2026-10-06 | open |
| Fabien | First harvest hour; target 10 cards | 2026-10-10 | open |

## Open questions

- Anonymous publication (device id + moderation queue) if the login wall loses more than half of the submitters: CEO decision once measured, not before.
- Which French freelance communities allow member posts about side projects? (Unchanged; channel map, week 4.)

## Related wiki pages

- Syntheses: [freelance deck v1](../projects/2026-09-11_freelance-deck-v1.md), [structure & dedup spec](../projects/2026-09-11_problem-structure-dedup-spec.md), [rollout playbook](2026-09-11_community-rollout-playbook.md), [90-day plan](2026-09-11_launch-plan-90-days.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Live read of `xeonfab/fix-it-karma` on 2026-09-11 (`src/components/ouch/submit-flow.tsx`, `src/routes/communaute.independants.index.tsx`, `docs/persistence-spec.md`)
- [raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md](../../../raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 community-rollout-playbook](2026-09-11_community-rollout-playbook.md)
- [2026-09-11 freelance-deck-v1](../projects/2026-09-11_freelance-deck-v1.md)
- [2026-09-11 freelance-deck-v1 expert-review](../projects/2026-09-11_freelance-deck-v1_expert-review.md)
- [2026-09-11 launch-plan-90-days](2026-09-11_launch-plan-90-days.md)
- [2026-09-11 problem-structure-dedup-spec](../projects/2026-09-11_problem-structure-dedup-spec.md)
- [2026-09-11 team-skills-audit](2026-09-11_team-skills-audit.md)
- [2026-09-12 freelance-channel-map](2026-09-12_freelance-channel-map.md)
- [2026-09-14 reddit-harvest-pipeline](../projects/2026-09-14_reddit-harvest-pipeline.md)
- [channel-tracking](../research/channel-tracking.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
