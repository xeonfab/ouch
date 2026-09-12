---
last_reviewed: 2026-09-12
---

# Entity pages vs the Maker space — what is public, what is sold, who creates an entity page

> One-line TL;DR: the panel settled the design strategy of the two non-victim surfaces. An **entity page** is the complete, public, free listing of every published card tied to one organisation (top 3 expanded, the rest folded, never hidden behind a payment); the **Terminal Maker** is the maker workspace where the intent data (opt-in counts and access, trends, demographics, export, alerts) will be sold once the Cercle 2 signal exists. Hiding cards behind a paywall was refused on legal and cold-start grounds. Entity pages are **created editorially by Ouch!**, never claimed by the entity and never auto-created; the bridge for organisations not yet in the registry is a private `entity_candidate` field filled by the qualifier, not the hashtag.

| Field | Value |
|---|---|
| **Date** | 2026-09-12 |
| **Type** | strategy (panel decision) |
| **Participants** | Fabien (founder); `panel-ouch-double-face` — Karim (CEO), Yasmine (growth), Marc (CTO), Léa (victim), Julien + Nadia (makers); invited seats at the founder's request: `ouch-legal`, `ouch-cfo`, `ouch-ux-designer`, `ouch-editeur-cartes` |
| **Source(s)** | [raw/transcripts/2026-09-12_reflexion-pages-entite-espace-maker.md](../../../raw/transcripts/2026-09-12_reflexion-pages-entite-espace-maker.md); live read of `xeonfab/fix-it-karma` `main` (`924f93f`) on 2026-09-12 |

---

## Context

Fabien asked three things: (1) clarify the design strategy of the modules for makers versus the pages for entities; his mental model was an entity page as "the official page gathering that entity's problems", showing only a few problems plus a total, the rest visible only after paying for the Maker space, and whether that is legally viable; (2) how an entity page gets created, manually by the entity itself ("officialising its access and identity") or automatically; (3) if manual, whether hashtags should serve, at first, to target problems about an organisation not yet in the registry.

The panel skill normally invites one extra seat; the founder asked for the whole team, so four seats were invited (legal, CFO, UX, card editor). Léa and Julien/Nadia spoke as the two personas.

### What the live code does today (Marc's read, `main` on 2026-09-12)

| Surface | State | Consequence |
|---|---|---|
| `/entite/:slug` | Header with 4 counters (problems, average pain, cumulated pain, people concerned) + "N attendent une solution"; then **top 3 cards** labelled « Vue publique · aperçu »; then a dashed block « 🔓 Vue détaillée Maker » listing **all** cards with votes, leads, and `devWeeks` — **open to everyone, no gate** | The teaser + maker view is already half-built as a visual mock. It mixes the two registers on one victim-side page and shows a fabricated number (`devWeeks`) |
| `/terminal` | Open, no login (D4); filters by sector/topic/status; brief panel with leads count and a mock "Claim this Problem & Unlock N Leads" button | No entity filter; no path from an entity page to the Terminal |
| `/devenir-maker` | **Route does not exist** in the repo (the 2026-09-10 snapshot and the launch plan still cite it as "pricing soon + email capture") | There is no maker email capture surface at all today; the wiki was stale on this point |
| Entity registry | Closed list in `entities.ts` (13 real organisations, `aliases`), page exists only if a published card links to it | Correct per the dedup spec §5 |
| Qualifier (`qualifyProblem`) | Returns `entity_slug` only from the closed list; a story naming an organisation absent from the registry yields `null` and **the name is lost** for moderation (it stays only inside the statement text) | Nothing today collects "which organisations are named but not registered" |
| Events | No `entity_page_visit`; `terminal_visit` carries `referrer` | Entity-page share cannot be measured |

## Anchor (repeated to every seat at every round)

> **Risk in play**: gating the cards of an entity page behind a paid Maker space, and building an entity-claim flow, would spend Phase 1–2 build hours on a maker side that has zero demand yet (0 real makers, votes from one device), would remove from the victim side the one surface Yasmine counts on for zero-CAC sharing and SEO, and would reintroduce an "official entity" status that hard rules 4–5 forbid. **Opportunity**: a clean split makes the entity page the free share hook and the Terminal the only place where maker data lives, so that the paywall, when the Cercle 2 signal comes, has a line that is already drawn.
>
> **Stage**: 82 published cards, 13 real entities, votes from Fabien's device only, 0 makers, Phase 1 of the 90-day plan; D4 (no paywall before the Cercle 2 signal) and D5 (feature freeze) in force.

## Round 1 — independent opinions

**Karim (CEO)** — ⚠️. The "few cards + total, pay to see the rest" idea confuses two surfaces that serve two sides. The entity page serves the victim side and the share loop; the Terminal serves makers. The blocker: it violates D4 and the settled 2026-09-11 rule that every problem tied to an entity appears on that entity's page. Simplification: keep the teaser as a *presentation* (top 3 open, the rest folded, all public) and move the "what is sold" question to the Terminal. Serves cold start now? Only the presentation part does; the paywall assumes volume that does not exist.

**Yasmine (growth)** — ❌ on the paywall, ✅ on the split. People share a page with a big number; nobody shares a paywall. The entity page is the zero-CAC surface (LinkedIn share, SEO on the organisation's name). Blocker: hiding cards kills the share and the SEO body text. Also, the hashtag cannot target an unregistered entity: the rule says a hashtag never names an entity, so using it as an entity bridge breaks the rule the day it works. Simplification: a maker CTA at the bottom of the entity page towards the Terminal, and an `entity_page_visit` event so shares can be counted per channel.

**Marc (CTO)** — ✅ conditional. The split costs almost nothing: the public part exists; the fake maker block must go (it shows `devWeeks`, a number the catalog invents). A gate on the Terminal is a day of work (auth + plan table) and is not for now. An entity-claim flow with identity verification is two days plus a permanent support burden; an auto-creation flow needs the qualifier to invent slugs, which the legal grid forbids. Simplification: one nullable column `entity_candidate` on `problems`, filled by the qualifier when the story names an organisation absent from the registry; a weekly query groups candidates; Fabien promotes by hand. Two hours.

**Léa (victim)** — « Je vais sur la page Qonto pour voir si ma galère y est déjà. Si je vois trois cartes et "44 autres, payez pour voir", je ferme. Trois cartes puis "voir les 44 autres", ok, je déplie. Et si le chiffre en haut est gros, je l'envoie à mon collectif. » **Swipe à gauche** on the paywall version, **swipe à droite** on the folded one.

**Julien (maker, Type A)** — « Un teaser à trois cartes avec "payez pour voir la suite" sur un site où personne n'a encore voté, je ris et je retourne sur Reddit. Ce que je paierais un jour : les emails opt-in, la tendance sur sept jours, l'export. Pas la liste des cartes, que je peux lire gratuitement partout. Si tout est public sauf les emails et la tendance, la ligne est claire et je comprends ce que j'achète. » **Je reviendrais voir plus tard**, when there is volume.

**Nadia (maker, Type B, PM inside a named entity)** — « Une page qui cache des plaintes sur ma boîte derrière un paiement, je la transfère au juridique et je ne reviens jamais : ça se lit "payez pour savoir ce qu'on dit de vous". Une page où tout est visible, factuel, sans note, je la mets dans mon backlog, et je paierais le Terminal pour le volume et la tendance comparés à ce que mon support me remonte. Un bouton "revendiquer cette page" ? Je ne le cliquerais pas, et mon juridique me demanderait ce que ça engage. » **Je paierais** the data version, **je passe mon chemin** on the gated version.

**`ouch-legal`** — ❌ on gating cards, ✅ on selling data. Nothing prevents Ouch! from monetising a database it produces. But the specific construction "some complaints about X are visible, the rest are behind a payment" changes the regime twice: (a) it reads as a pressure device towards the named organisation ("pay to see what is said about you"), the reputation-management regime the product has always refused, with a far heavier exposure than a neutral listing; (b) selective display looks like an editorial ranking, which weakens the "neutral factual signal" defence. The safe construction is the opposite: **total transparency of the cards** (nothing hidden = nothing to accuse Ouch! of hiding or trading), and what is sold is analysis and intent data as a service to any maker, the entity included, without a status. On creation: an entity that "officialises its identity" is an official account; hard rule 4 forbids it, and it would create the expectation of a right of reply and of moderation rights (the Trustpilot regime). Auto-creation is refused too: a page must not exist for a misspelled, hallucinated or non-public organisation; the registry rule (public name, attributable friction, logged source) needs a human look. Two things to add regardless of this decision: a « signaler cette carte » notice link on every card (hosting-platform obligation, one-way, not a reply), and the consent copy update before any opt-in access is sold.

**`ouch-cfo`** — ⚠️. D4 stands: no paywall before the Cercle 2 signal. But drawing the line now on paper costs nothing and tells us what to instrument. Free forever: everything on the entity page. Paid later, 15–40 €/month: per-card opt-in count and access (with the consent update), 7-day trend, demographics from `survey_answers`, CSV export, alerts on an entity or a card. A maker pays for time saved and for intent, never for reading complaints.

**`ouch-ux-designer`** — ✅ on the split, with one removal. The current page mixes the two registers: a playful victim-side page that ends in a dashed "maker" block. Proposal: keep the capturable number in the header, top 3 cards, a fold « Voir les N autres galères », and **one** maker CTA at the bottom in Terminal style (dark strip): « Analyser #Qonto sur le Terminal Maker → ». Remove the maker block from the page.

**`ouch-editeur-cartes`** — ✅ on the candidate field. The hashtag rule stays absolute (context only). A card that names an unregistered organisation in its statement is fine under the card standard when the author is identified (first-person lived fact, signed) or when a source is logged (harvested cards). The name in the text is the public trace; the private `entity_candidate` is the moderation trace. Promotion to the registry: two published cards naming the same organisation, or one card with ≥10 🔥, then the legal look, then a script backfills `entity_slugs` on those cards. Never a page from a single unsourced mention.

## Round 2 — confrontation (President)

Three tensions, one mandatory check.

1. **Teaser as a paywall vs teaser as a layout** (Fabien's model vs Karim/Yasmine/Léa/legal). Does anything of value for the maker side get lost if every card is public? Addressed to Julien, Nadia, CFO.
2. **Who creates an entity page** (entity claims it / automatic / editorial). Addressed to legal, Marc, card editor: is there a version of "the entity officialises itself" that respects hard rule 4, and what does automatic creation cost in legal exposure?
3. **The hashtag as a bridge** for unregistered organisations. Addressed to card editor, Marc, Yasmine: what carries the name of an unregistered organisation, publicly and privately?

Cold-start check: the paywall defers the value to "when there is volume", an unvalidated hypothesis; the split and the candidate field serve the cold start this week (the share surface stays whole, the qualifier stops losing names). The paywall is therefore treated as a hypothesis for the Cercle 2 signal, not as a design input for now.

## Round 3 — co-construction

**On tension 1** — Julien: nothing is lost; the card list has no resale value, the intent data has. Nadia: the public list is what makes her trust the page; the paid part is the comparison with her own support volume. CFO: the paid perimeter is therefore *data about the cards*, never *the cards*; the entity page shows aggregate intent (« N attendent une solution ») as the hook, and per-card opt-in counts, trends and exports live on the Terminal. Everyone agrees the Score de Douleur `/100` stays visible on the entity page (already the rule of the dedup spec §7) because it is the number a maker screenshots.

**On tension 2** — Legal: no. Any flow in which an organisation proves it is the organisation creates an account with a status, whatever it is called, and the product's whole defence is that no such status exists. The entity can subscribe to the Terminal like any maker, with a personal account, and gets nothing more. Marc: automatic creation needs the qualifier to emit a new slug; the model will emit "Shine", "shine.fr", "la banque Shine" as three entities, and a page will exist within the minute for whatever a visitor typed. Card editor: editorial creation from a queue is what the registry rule already says; the missing piece is the *input* of that queue. **Resolution: editorial creation only**, fed by the candidate field; page appears when ≥1 published card links (already built).

**On tension 3** — Card editor: the hashtag keeps its job (context: `#SeuilTVA`, `#RelanceFacture`), the organisation's name keeps living in the statement text (public, honest, first-person), and the private `entity_candidate` field carries the normalised name for moderation. Marc: the qualifier gets one more structured output, `entity_candidate: string | null`, with the same guard as `entity_slug` (never a person, never a category); the column is private (no client read policy), the weekly moderation query groups it. Yasmine: the weekly count of candidates is also a growth signal: the organisations freelances name most are the next entity pages, hence the next share surfaces.

## Round 4 — final synthesis (President)

```
════════════════════════════════════════════════
🎯 PANEL OUCH! — PAGES ENTITÉ VS ESPACE MAKER
════════════════════════════════════════════════

📋 LA DÉCISION BRUTE EN UNE PHRASE
Faire de la page entité un teaser (quelques cartes + un total) dont la suite
se paie dans l'espace Maker, et laisser l'entité créer sa page en officialisant
son identité, avec les hashtags comme pont vers les entités non enregistrées.

────────────────────────────────────────────────
🔄 CE QUI A CHANGÉ PENDANT LA DÉLIBÉRATION
────────────────────────────────────────────────
→ Tension : le teaser payant sur les cartes contredit D4, la règle « toute
  carte liée à une entité apparaît sur sa page », et fait glisser le produit
  vers le régime « payez pour savoir ce qu'on dit de vous » (juriste, Nadia).
→ Résolution : le teaser reste une mise en page (3 cartes ouvertes, le reste
  plié, tout public) ; ce qui se vendra, ce sont les données d'intention sur
  le Terminal, jamais les cartes. La création de page est éditoriale, jamais
  revendiquée ni automatique ; le pont vers une entité absente du registre est
  un champ privé `entity_candidate`, pas le hashtag.

════════════════════════════════════════════════
🏆 DÉCISION FINALE CO-CONSTRUITE
════════════════════════════════════════════════

DÉCISION RETENUE (1 phrase)
Deux surfaces, deux métiers : la page entité est le listing public et complet
(registre victime, chiffre capturable, cartes pliées au-delà de trois, un seul
CTA maker vers le Terminal) ; le Terminal Maker est l'espace de travail des
makers où vivront, puis se vendront, les données d'intention ; une entité entre
au registre par la file éditoriale de Fabien, alimentée par le champ privé
`entity_candidate` que le qualifieur remplit quand un récit nomme une
organisation inconnue.

CÔTÉ(S) DU MARCHÉ SERVI(S) EN PRIORITÉ
Victimes maintenant (la page reste partageable et complète : une freelance y
retrouve sa galère et rejoint la carte) ; makers dans un second temps (une
ligne gratuit/payant déjà tracée, un chemin page entité → Terminal mesuré).

COHÉRENCE RISQUE → DÉCISION
La décision sert le cold start cette semaine : la surface de partage reste
entière, le qualifieur cesse de perdre les noms d'organisations, et rien n'est
construit pour un acheteur qui n'existe pas encore. Le paywall reste une
hypothèse à valider au signal Cercle 2, pas un acquis.

CE QU'ON NE FAIT PAS MAINTENANT (exclusions explicites)
→ Aucun paywall, aucune page prix, aucune porte sur le Terminal avant le
  signal Cercle 2 (D4).
→ Aucun flux « revendiquer / officialiser cette page » pour une entité, jamais
  (règle dure 4) ; aucune création automatique d'entité par le qualifieur.
→ Aucun filtre « entité » dans le Terminal avant qu'un maker le demande en
  Phase 3 (D5 : pas de nouveau filtre avant J+90).
→ Aucune vente d'accès aux emails opt-in sans mise à jour du texte de
  consentement.

TEMPS RÉEL ESTIMÉ (Marc)
~4 h avant le 2026-10-01 (page entité repliée sans bloc maker, événement
`entity_page_visit`, colonne + sortie du qualifieur `entity_candidate`,
requête hebdo) ; ~1 h en Phase 3 (capture email maker sur le Terminal) ;
~1 jour au signal Cercle 2 (porte + plan + consentement). Compatible 20 h/sem.

CANAL D'ACQUISITION CONCERNÉ (Yasmine)
Partage LinkedIn / collectifs de la page entité (test public de la semaine 7,
`?c=` par canal) ; SEO sur le nom de l'organisation ; la file de candidats
donne les prochaines pages à ouvrir.

RÉACTION VICTIME (Léa) / RÉACTION MAKER (Julien)
Léa : « trois cartes, "voir les 44 autres", le gros chiffre en haut : je
déplie et je l'envoie au collectif ». Julien : « tout public sauf les emails
et la tendance : je comprends ce que j'achèterai, je reviens quand il y a du
volume ».

MÉTRIQUE DE SUCCÈS MESURABLE
→ Semaine 7 : ≥1 page entité partagée avec un compteur réel, ≥50
  `entity_page_visit` sur un `?c=` de partage, ≥3 `terminal_visit` dont le
  referrer est une page entité.
→ Chaque dimanche : nombre d'organisations candidates distinctes ; ≥1
  promotion au registre par mois en Phase 2.

VERDICT FINAL
GO ✅ sur la clarification et les ~4 h de travaux ; NON ❌ sur le teaser
payant et sur la revendication de page par l'entité ; REPORT 🔄 du paywall au
signal Cercle 2, avec la ligne gratuit/payant ci-dessous déjà tracée.
════════════════════════════════════════════════
```

## The surface map (the deliverable)

| Surface | Audience & register | Job | Always free | Paid later (Terminal Pro, after the Cercle 2 signal) | Never |
|---|---|---|---|---|---|
| `/communaute/:slug`, `/swipe`, home | Victims · fun | Swipe, join a card, submit | Everything | — | Terminal styling, any number the visitor cannot move |
| **`/entite/:slug`** | Victims first, makers as visitors · fun, capturable | Public, complete listing of one organisation's canonical cards; share and SEO surface; entry point to the Terminal | Header number « N concerné(e)s », « N attendent une solution » (aggregate), Score de Douleur per card, status, Type A/B badge, voices, **all** published canonical cards (top 3 expanded, the rest folded), « signaler cette carte » | — (nothing on this page is ever gated) | Rating, ranking between entities, reply box, claim button, official badge, per-card opt-in counts, `devWeeks` or any invented number, maker-register blocks |
| **`/terminal`** | Makers (independents = Type A, intrapreneurs = Type B) · factual, dark | Find a validated problem, compare, follow, export | Until the signal: everything visible, no login (D4); after: ranking, Score de Douleur, counters, card text | Per-card opt-in count and **access** (consent copy updated first), 7-day trend, demographics from `survey_answers`, CSV export, alerts « suivre cette entité / cette carte », entity filter | Confetti, Karma, any victim-side gamification; any status for a subscribed entity |
| Maker email capture | Makers · factual | « Prévenez-moi à l'ouverture du Terminal Pro » | Free | — | A pricing page before the signal |
| Entity registry | Internal | Real, public organisations only | — | — | Placeholder, category, person, self-registration |

Rule of thumb, in one sentence for the CGU and the pitch: **the cards are public, the intent data is sold.**

## Entity lifecycle (editorial, never claimed, never automatic)

```
story names an organisation
        │
        ├─ organisation in the registry (slug or alias) ──▶ qualifier proposes the chip
        │                                                    ▶ author confirms « Lier à l'entité X ? »
        │                                                    ▶ card published with entity_slugs
        │                                                    ▶ page /entite/X shows it (already built)
        │
        └─ organisation unknown ──▶ qualifier sets entity_candidate = "Shine"   (private)
                                    ▶ card published with the name in its text, no chip, no page
                                    ▶ Sunday query: candidates grouped by normalised name, count, 🔥
                                    ▶ threshold: ≥2 published cards OR 1 card ≥10 🔥
                                    ▶ ouch-legal look: public name? attributable friction? source logged?
                                    ▶ Fabien adds the entry to entities.ts (name, aliases, type, sector)
                                    ▶ script backfills entity_slugs on the candidate cards
                                    ▶ page appears (≥1 published card linked)
```

A person is never a candidate (existing guard). A category (« ma banque ») is never a candidate. An organisation that later subscribes to the Terminal changes nothing on this path.

## Build sequence under D5

| Change | Class under D5 | Owner | When | Estimate |
|---|---|---|---|---|
| Entity page: remove the « Vue détaillée Maker » block and `devWeeks`; fold cards beyond 3 with « Voir les N autres galères »; one Terminal-style CTA at the bottom | legal/consistency fix (an invented number on a public page; register mix) | `ouch-cto` + `ouch-ux-designer` | ≤ 2026-10-01 | 1.5 h |
| `entity_page_visit` event with `props.utm`; `terminal_visit` already carries `referrer` | instrumentation (D5-c) | `ouch-cto` | ≤ 2026-10-01 | 0.5 h |
| `entity_candidate text` column (private, no anon read), qualifier output, Sunday query in `docs/metrics.sql` | instrumentation (D5-c): the qualifier drops information today | `ouch-cto` | ≤ 2026-10-01 | 2 h |
| « Signaler cette carte » link (mailto or form, one-way) on card detail and entity page | legal obligation (D5-b) | `ouch-legal` wording, `ouch-cto` | Phase 2, before the week-7 share test | 1 h |
| Maker email capture on the Terminal (« Prévenez-moi à l'ouverture du Terminal Pro ») | Phase 3 need (replaces the missing `/devenir-maker`) | `ouch-cto` | week 8 | 1 h |
| Entity filter in the Terminal | new filter: only if a Phase 3 maker asks | `ouch-cto` | Phase 3 or after day 90 | 2 h |
| Terminal Pro gate, plan table, consent copy update, pricing page | product decision at the Cercle 2 signal | `ouch-cfo`, `ouch-legal`, `ouch-cto` | after the signal | 1 day |

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Confirm the three decisions: cards public / data sold; editorial creation, no claim flow; `entity_candidate` as the bridge | 2026-09-14 | open |
| Claude Code (`ouch-cto`) | Branch: entity page fold + CTA + `entity_page_visit` + `entity_candidate` (column, qualifier, query) | 2026-10-01 | open |
| `ouch-legal` | Wording of « Signaler cette carte » and the future consent line for opt-in access | 2026-10-15 | open |
| Fabien + `ouch-editeur-cartes` | Sunday: read the candidate query, promote per the threshold | from 2026-10-12 | open |
| Wiki | Correct the stale `/devenir-maker` mentions (full context page, launch plan) | 2026-09-12 | **done in this page and the MOC** |

## Open questions

- Should the aggregate « N attendent une solution » stay on the public entity page, or is it already maker data? Panel default: **stays public as an aggregate** (it is the intent hook Yasmine and Karim count on); per-card counts go to the Terminal.
- Threshold for promoting a candidate (2 cards, or 1 card with ≥10 🔥): to adjust after four Sunday reads.
- When the Terminal Pro opens, does an entity page get a « voir la tendance sur le Terminal » deep link per card, or only the page-level CTA? Decide with the pricing design, not before.

## Related wiki pages

- Syntheses: [rollout playbook](2026-09-11_community-rollout-playbook.md) (entities = the product's entités, two maker profiles), [90-day plan](2026-09-11_launch-plan-90-days.md) (D4, D5), [problem structure & dedup spec](../projects/2026-09-11_problem-structure-dedup-spec.md) (registry rules §5, presentation rules §7), [full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md) (hard rules 4–7)
- Concepts: [Resolution Type A/B](../../concepts/Resolution_Type_AB.md), [Score de Douleur](../../concepts/Score_de_Douleur.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- [raw/transcripts/2026-09-12_reflexion-pages-entite-espace-maker.md](../../../raw/transcripts/2026-09-12_reflexion-pages-entite-espace-maker.md)
- Live read of `xeonfab/fix-it-karma` (`main`, `924f93f`, 2026-09-12): `src/routes/entite.$slug.tsx`, `src/routes/terminal.tsx`, `src/routes/` (no `devenir-maker`), `src/lib/entities.ts`, `src/lib/qualify.functions.ts`, `src/components/ouch/submit-flow.tsx`, `src/components/terminal/brief-panel.tsx`

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
