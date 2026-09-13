---
last_reviewed: 2026-09-13
---

# Facebook finance group — first group post (pre-flight + copy)

> One-line TL;DR: Fabien wants to post in a Facebook group described as a "finance community" (share link `facebook.com/share/g/19qoQFPgcm`, unreachable from the build sandbox, so the group's name, size and rules are unverified). This page gives the go/no-go checks in order (product gate, group fit, admin, legal, tracking) and the ready-to-paste French copy: admin DM, post, first comment with the link, replies. Channel value `?c=fb-finance`.

| Field | Value |
|---|---|
| **Date** | 2026-09-13 |
| **Type** | strategy (distribution, wave 2 brought forward) |
| **Participants** | Fabien (founder), `ouch-growth-hacker` (Yasmine, copy), `ouch-persona-victime` (Léa, 2-second test), `ouch-legal` (grid) |
| **Source(s)** | [channel communication plan](2026-09-11_freelance-channel-communication-plan.md) §3.2 and §6; [channel map v0](2026-09-12_freelance-channel-map.md); [freelance deck v1](../projects/2026-09-11_freelance-deck-v1.md) sections C–D; [90-day plan](2026-09-11_launch-plan-90-days.md) Phase 1 gate; `wiki/log.md` entries of 2026-09-12 (Vercel live, field check) |

---

## Context

The plan schedules Facebook groups as wave 2 (week 5), after a LinkedIn wave on Fabien's own network. Fabien wants to start with this group now. That is acceptable under the plan's rules as long as the same guardrails apply: ask the admin first, post as a member, one post per group ever, card-first copy, its own `?c=` value. What changes is only the order of the waves; it is logged here so the Sunday metrics read correctly.

What the wiki knows about the state of the product on 2026-09-13:

- Production is live on Vercel at `fix-it-karma.vercel.app`, on the founder's own Supabase project; votes, opt-ins, events and submissions land (field check of 2026-09-12, one device, `?c=test`).
- The Phase 1 exit gate is **not formally passed**: the second-device test and the 5 friendly freelances are still open in the launch plan.
- The freelance deck (54 cards, 10 in the launch deck) is inserted and published, every entity-named card has a logged source.
- PR #8 (ranked lists frozen during a visit, card votes tagged) was opened on 2026-09-12; its merge state is not recorded in the wiki.

## 1. Pre-flight checks, in order (stop at the first red)

### A. Product gate (10 minutes, non-negotiable)

| # | Check | Why | How |
|---|---|---|---|
| A1 | **Two-device test**: open `/communaute/independants?c=test` on the phone, swipe one card right, see the same counter on the laptop | The whole point of Phase 1; never proven on two devices | Card 1 (relances impayés) is the safest |
| A2 | **Purge or keep the `?c=test` rows** (Fabien's 14 votes, 7 opt-ins, card 86 without community tag) | First real visitors must not see the founder's own votes as social proof; card 86 sits untagged in the registry | Decide; the purge SQL is in the launch plan; if kept, tag card 86 `independants` by hand |
| A3 | **Live check of the page on the phone**: deck loads (10 cards, curated order), « Moi aussi 🔥 » button, Google opt-in after a right swipe, « Déposer ma frustration » reaches the preview | PR #7 and #8 changed the card and the ranking; a broken deck on mobile burns the one post allowed in this group | Facebook traffic is mostly mobile |
| A4 | **Submission works in production** (Anthropic key and Google OAuth set in Vercel) | Verified 2026-09-12 (one card published through the qualifier); re-check only if Vercel env vars changed since | — |
| A5 | **No invented number anywhere on the page** | A finance audience reads numbers first; a fake counter kills credibility | Counters were zeroed at migration; glance at the ranked list |

### B. Group fit (the link could not be opened from the sandbox)

| # | Check | Decision rule |
|---|---|---|
| B1 | **Who is in it?** Finance *professionals* (experts-comptables, DAF à temps partagé, consultants finance, contrôleurs de gestion) or *personal finance* (épargne, bourse, immobilier)? | Finance professionals: **go**, many of them are freelances themselves and the rest accompany freelances and TPE daily, so the freelance deck fits. Personal-finance / investing group: **no-go**, that is Cercle 3 (grand public), which the plan keeps off-limits before day 90; do not spend the group's one post on the wrong deck. |
| B2 | **Rules**: self-promotion, external links, "projet perso" posts, posting days | Links forbidden in posts → link goes in the first comment (copy below already assumes it). Self-promotion forbidden outright → ask the admin anyway with the DM below; if refused, harvest only (reply in threads, no link). |
| B3 | **Size and activity** (members, posts per day) | Under ~1 000 members or no post in the last week: still fine as a test, but expect single-digit voters; do not read the channel ranking from it. |
| B4 | **Fabien posts as a member from his personal profile**, never from a page | Plan rule: post as a member, not as a brand |
| B5 | **Is Fabien already an accepted member?** | If just joined, wait a few days and answer one or two threads first (the Slack rule, cheap on Facebook too) |

### C. Admin first (mandatory), one post ever

Send the DM in section 2 to an admin or moderator **before** posting. Then one post, and only replies in other people's threads afterwards. Leave if asked.

### D. Legal and copy (from the moderation grid)

- The three quoted cards are **entity-free, Type A** (F01 relances, F18 seuil de TVA, F34 revenus irréguliers): no organisation in the hook, as the plan requires. Do not quote the Qonto or Stripe cards in the post, even if they perform well on the page.
- No company tagged, no « pire banque / pire logiciel » angle, no policy stance (TVA and URSSAF appear as lived administrative facts only).
- No promise that a problem gets solved; the only promise is « tu seras prévenu si quelqu'un s'en empare ».
- Comments that describe a friction are **harvested and rewritten** to the card standard, never republished verbatim; a card that names an organisation needs a row in the [sourcing sheet](../research/sourcing-sheet-entity-cards.md) first.
- The opt-in consent copy on the page stays « être prévenu d'une solution »; no other use of the emails.

### E. Tracking

- Link: `https://fix-it-karma.vercel.app/communaute/independants?c=fb-finance`. Rename the value to `fb-<short group name>` once the group is identified, and add the row to the [channel map](2026-09-12_freelance-channel-map.md) (a placeholder row exists).
- Sunday metrics row for this channel: distinct voters, positive rate, opt-in rate, submissions, harvested cards, proxy submissions confirmed (targets in the plan §7).
- Reply to every comment within the day; every comment describing a friction becomes a card by Friday, then a DM « je l'ai ajoutée, c'est bien ta galère ? » with the card link (proxy submission).

## 2. Copy (French, ready to paste)

### 2.1 Admin DM

> Bonjour, je suis membre du groupe et je travaille sur un projet perso, sans but commercial à ce stade : recenser les galères d'argent et d'admin des indépendants (impayés, TVA, trésorerie, compte pro…) pour qu'elles arrivent aux bonnes personnes. Est-ce que je peux poster une fois un lien vers un test de 20 secondes (pas de compte, pas de pub) ? Je respecte évidemment votre réponse.

### 2.2 The post (link in the first comment)

> Salut à tous 👋
>
> « Chaque vendredi, je perds trois heures à relancer mes factures impayées. »
> « J'ai dépassé le seuil de TVA en cours d'année sans m'en rendre compte : trois factures à refaire. »
> « Un mois à 8 000 €, le suivant à 0 € : rien ne me dit ce que je peux vraiment me verser. »
>
> Question sérieuse pour ceux qui bossent en indépendant (ou qui en accompagnent au quotidien) : c'est quoi la galère d'argent ou d'admin que vous n'arrivez toujours pas à régler ?
>
> Sur mon temps libre, j'ai mis les 10 galères que j'entends en boucle sous forme de cartes à swiper : droite si ça vous arrive, gauche sinon. 20 secondes, pas de compte. Le but : compter combien de personnes ont exactement la même galère, pour qu'elle finisse sous le nez de gens qui construisent des solutions. Et vous êtes prévenu si une sort.
>
> 👉 Le lien est en premier commentaire.
>
> Si la vôtre n'y est pas, dites-la-moi en commentaire, je l'ajoute. Et un retour franc (même « aucun intérêt ») m'aide beaucoup 🙏

If the group allows links in posts, replace the « 👉 » line with:

> 👉 https://fix-it-karma.vercel.app/communaute/independants?c=fb-finance (20 secondes, pas de compte)

### 2.3 First comment (posted right after the post)

> 👉 https://fix-it-karma.vercel.app/communaute/independants?c=fb-finance
> 10 cartes, 20 secondes, pas de compte. Le projet s'appelle Ouch! : ici, râler sert à quelque chose.

### 2.4 Replies to the usual comments

| Comment | Reply |
|---|---|
| « C'est quoi l'intérêt pour moi ? » | « Voir que t'es pas seul, et être prévenu si quelqu'un construit une solution. C'est tout, et c'est gratuit. » |
| « Vous faites quoi de mon email ? » | « Uniquement te prévenir si une solution sort pour cette galère précise. Rien d'autre, c'est écrit au moment où tu le laisses. » |
| « Encore une plateforme… » | « Pas de compte pour swiper. 20 secondes. » |
| « Ça sert à rien de râler » | « Ici ça sert à un truc précis : compter combien de personnes ont exactement la même galère, pour que quelqu'un la prenne au sérieux. » |
| « Vous allez balancer des boîtes ? » | « Non. On décrit des faits vécus, jamais un jugement sur une boîte. Une entreprise nommée peut d'ailleurs venir lire ce qui remonte, comme n'importe qui. » |
| Someone describes their own friction | « Merci, je l'ajoute en carte et je te l'envoie pour que tu me dises si c'est bien ça. » → harvest, rewrite, DM with the card link |
| An accountant describes a client's friction | Same as above; the card stays first person from the freelance's point of view, the accountant is never named |

### 2.5 Léa's two-second read

Opens on three sentences she could have said herself, the ask is « laquelle est la vôtre ? » not « inscris-toi », the product name appears once, in the comment. Three quotes is the ceiling; a fourth makes it a listicle.

## 3. Why these three cards

| Card | Why it opens the post | Sector · Topic |
|---|---|---|
| F01 relances impayés (3 h chaque vendredi) | The one every freelance and every accountant recognises; opens with a sure « moi aussi » | Fintech · Facturation |
| F18 seuil de TVA dépassé | The finance-flavoured surprise; strong Type A signal for makers | B2B · Finance/Compta |
| F34 8 000 € puis 0 € | Cash-flow smoothing is the topic a finance audience will argue about in the comments, which is what we want | Fintech · Budget |

Alternates if the group is more « micro-entrepreneur » than « finance pro »: F33 (combien mettre de côté), F21 (CFE de décembre), F26 (200 lignes de relevé perso/pro).

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | A1–A3: phone test on the same card, decide the `?c=test` purge, check the deck on mobile | before posting | open |
| Fabien | B1–B2: identify the group (name, audience, rules), write it in the channel map row `fb-finance` | before posting | open |
| Fabien | Send the admin DM; post on the next Tuesday morning after a yes; first comment with the link | after the admin's yes | open |
| Fabien | Reply to every comment within the day; Friday harvest hour on the thread; Sunday metrics row `fb-finance` | week of the post | open |
| `ouch-ceo` | Log the wave-order change (Facebook before LinkedIn) at the Sunday review | next Sunday | open |

## Open questions

- Is the group finance professionals or personal finance? (Decides go/no-go, rule B1.)
- Was PR #8 merged before the post? If not, the ranked list still re-sorts under the cursor; not blocking for a swipe-first post, but the phone check in A3 should look at it.

## Related wiki pages

- Syntheses: [channel communication plan](2026-09-11_freelance-channel-communication-plan.md) (§3.2 Facebook groups, §4 harvest, §6 objections), [channel map v0](2026-09-12_freelance-channel-map.md), [freelance deck v1](../projects/2026-09-11_freelance-deck-v1.md), [90-day plan](2026-09-11_launch-plan-90-days.md), [test de concept — communauté freelances](2026-09-10_test-concept-communaute-freelances.md) (earlier, longer message for a closed group)
- Research: [sourcing sheet](../research/sourcing-sheet-entity-cards.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Facebook share link `https://www.facebook.com/share/g/19qoQFPgcm/` (blocked by the sandbox's network policy; nothing read from it)
- `wiki/log.md`, entries 2026-09-12 (deploy, field, PR #6–#8)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-12 freelance-channel-map](2026-09-12_freelance-channel-map.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
