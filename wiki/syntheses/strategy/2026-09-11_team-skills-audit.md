---
last_reviewed: 2026-09-11
---

# Ouch! agent team — skills audit and upgrade (2026-09-11)

> One-line TL;DR: the nine Ouch! skills were auditable against the freelance push (deck, channels, structure) and came up short in four ways: none of them could auto-trigger (a YAML front-matter defect on all nine), the CTO still described a `localStorage` product, the CEO carried none of the six settled decisions, and three expertises the objective needs did not exist (French freelance domain, card editorship and moderation, growth analytics). All fixed today: nine skills updated, three created, twelve in the team.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | strategy |
| **Participants** | Fabien (founder), Claude Code |
| **Source(s)** | `skills/*/SKILL.md` on disk, the three workstream pages of 2026-09-11, the launch plan |

---

## Context

Fabien asked whether the team of skills is solid, whether each seat holds the sharpest expert for its domain, and to update, optimise or create skills wherever it does not. The yardstick is the objective: a first community (freelances) with high-quality problems collected on its channels, a communication strategy that gets freelances to submit, and a platform that presents and stores problems without duplicates or fuzz.

## 1. Coverage before the audit

| Need for the objective | Owner before | Verdict |
|---|---|---|
| Vision, priorities, gates | `ouch-ceo` | Solid persona, **outdated context**: no D1–D6, no loop, referenced Fabien's former employer |
| Channels, copy, cold start | `ouch-growth-hacker` | Solid levers, **no channel etiquette, no harvest protocol, no login-wall awareness** |
| Lovable/Supabase, build vs defer | `ouch-cto` | **Obsolete**: still described `localStorage` as the current state, no data-structure or dedup doctrine |
| Registers, screens | `ouch-ux-designer` | Solid, missing community-page and entity-page rules |
| Legal grid, entities, GDPR | `ouch-legal` | Solid, missing registry rules (placeholders), sourcing sheet, harvest rewriting |
| Pricing, monetisation timing | `ouch-cfo` | Solid, nothing needed for Cercle 1 |
| Victim reaction | `ouch-persona-victime` (Léa) | Good but **one profile**: creative in micro-entreprise; no voice for dev/consultant in SASU (TJM, ESN, portage) |
| Maker reaction | `ouch-persona-maker` (Julien) | Good but **one profile**: independent maker only; the founder's strategy also names intrapreneurs inside entities (Type B) |
| Structuring decisions | `panel-ouch-double-face` | Solid, five fixed seats, no way to bring a domain expert in |
| **French freelance domain accuracy** (URSSAF, TVA, CFE, e-invoicing, social protection, freelance ecosystem) | nobody | **Gap**: the 54 cards rest on fiscal/social facts nobody on the team could verify |
| **Card editorship and moderation** (standard, rewriting harvested complaints, dedup decisions, weekly moderation) | split between growth and legal | **Gap**: nobody owned quality and the canonical/duplicate decision |
| **Growth analytics** (weekly sheet, SQL on events, channel comparison, sample honesty) | nobody | **Gap**: the Sunday review had no analyst |
| Automation (Make/n8n scraping, week 6) | `ouch-growth-hacker` + generic `architecte-make-ia` skill | Covered by the existing generic skill; no Ouch-specific one needed before week 6 |
| Maker-side sales and outreach (Phase 3) | `ouch-growth-hacker` + Julien | Enough until Phase 3; revisit at day 60 |

## 2. Defect found on all nine skills: no auto-trigger

Every Ouch! skill declared its description as a folded YAML block (`description: >` followed by indented lines). The skill loader shows no description for those skills, while skills with a single-line quoted description show theirs. Without a description, the natural-language triggers ("que penserait Léa", "quelle priorité") cannot fire; the skill only works when invoked by name. Fixed by rewriting all nine descriptions (and `wiki-clean`, same defect) as single-line quoted strings, content unchanged.

## 3. What changed

### Updated (nine)

| Skill | Update |
|---|---|
| `ouch-ceo` | Removed the former-employer reference; added the six decisions D1–D6, the community rollout loop (entities as public listings, two maker profiles), the phase gates, the Sunday rule, and the list of experts to convene |
| `ouch-cto` | Rewritten context to the real state (Supabase persistence live, 7 tables, RLS insert-only, events with `?c=`, GitHub two-way sync, one driver on the code); fragile list from the live audit; doctrine on structure fixes, three-layer dedup, real-entities registry; retest list extended |
| `ouch-growth-hacker` | Added the Cercle 1 playbook: wave sequence with `?c=`, community etiquette, login wall and proxy submission, harvest protocol, copy rules, nevers, and the three new binômes |
| `ouch-legal` | Added registry rules (no placeholders, manual queue), mandatory sourcing sheet, harvest rewriting rule, hashtag rule, the four checks it owns in the card standard, no-reply/no-rating rule on entity pages, default position on anonymous publication |
| `ouch-ux-designer` | Added presentation rules for the community page, the entity page, the card hierarchy, the submission flow and shared content |
| `ouch-persona-victime` | Second voice **Sami** (dev freelance in SASU, Nantes: TJM, ESN, portage, unpaid tests); Léa stays the default |
| `ouch-persona-maker` | Second voice **Nadia** (intrapreneur, product manager in a fintech named on an entity page; judges Type B cards; no special status) |
| `panel-ouch-double-face` | Guest seat rule: one extra domain seat at rounds 1 and 3 when the decision needs it |
| `ouch-cfo` | Front-matter fix only |

### Created (three)

| Skill | Role | Why it is the missing expert |
|---|---|---|
| `ouch-expert-independants` | Expert-comptable / conseiller d'indépendants: statuts, URSSAF, TVA, CFE, facturation électronique, protection sociale, financement, ecosystem of French freelance communities; verifies every freelance card, maps the freelance "pain calendar", calibrates Type A/B | Cards live or die on factual accuracy in front of freelances who know their status; thresholds change yearly and must be dated and sourced |
| `ouch-editeur-cartes` | Chief card editor and moderator: owns the eight-check standard, rewrites harvested complaints, decides duplicates (canonical card, never deletion), composes community decks, runs weekly moderation | Quality and dedup had no owner; growth optimises volume, legal optimises risk |
| `ouch-data-analyst` | Growth analyst on the real schema: weekly sheet, SQL on `events`/`votes`/`leads`, channel comparison by `props.utm`, plan thresholds, sample honesty, login-wall measurement | The Sunday review decides the week; it needs one person who refuses vanity metrics and small samples |

## 4. Team after the upgrade (twelve seats)

| Seat | Skill | Workstream 1 · cards | Workstream 2 · channels | Workstream 3 · structure |
|---|---|---|---|---|
| CEO Karim | `ouch-ceo` | arbitrates | arbitrates | arbitrates |
| Growth Yasmine | `ouch-growth-hacker` | harvest | **lead** | — |
| Editor | `ouch-editeur-cartes` | **lead** | rewrite | dedup decisions |
| Freelance expert | `ouch-expert-independants` | **fact-check** | channel knowledge | Type A/B |
| Legal | `ouch-legal` | grid, sourcing | guardrails | registry |
| CTO Marc | `ouch-cto` | insertion | events | **lead** |
| UX designer | `ouch-ux-designer` | 2-second test | share content | presentation |
| Data analyst | `ouch-data-analyst` | card performance | **channel ranking** | dedup query |
| CFO | `ouch-cfo` | — | — | — (Phase 3) |
| Léa / Sami | `ouch-persona-victime` | swipe test | copy test | flow test |
| Julien / Nadia | `ouch-persona-maker` | Terminal value | — | entity page test |
| Panel | `panel-ouch-double-face` | — | — | structuring decisions |

## 5. Deliberately not created

- **Community manager**: folded into `ouch-growth-hacker` (etiquette, admin approach). A separate seat would split one person's channel work in two.
- **Automation engineer**: the generic `architecte-make-ia` skill already covers Make/Claude pipelines; an Ouch-specific brief is written in week 6 when the pipeline starts.
- **Maker sales / success**: Phase 3 concern; `ouch-growth-hacker` and Julien/Nadia cover the first ten conversations. Revisit at day 60.
- **Brand voice guardian**: the editor owns the card register, the UX designer owns the screen registers.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Claude Code | Fix front-matters, update nine skills, create three | 2026-09-11 | **done** |
| Fabien | Try three triggers in a fresh session (« que penserait Sami de cette carte ? », « vérifie la carte F18 », « feuille du dimanche ») and confirm the skills fire without being named | 2026-09-14 | open |
| `ouch-expert-independants` | First pass on the 54 cards: mechanism, figures, entity, Type A/B, frequency | 2026-09-17 | **done 2026-09-11** → [expert review](../projects/2026-09-11_freelance-deck-v1_expert-review.md) |
| `ouch-data-analyst` | Create the weekly sheet with the SQL of the skill; first empty row | 2026-09-14 | open |

## Open questions

- Should the generic `architecte-make-ia` skill get an Ouch section (schema, moderation queue) in week 6, or should an `ouch-automation` skill be created then? Default: a section, one less persona.
- At day 60, does Phase 3 need a maker-success seat?

## Related wiki pages

- Syntheses: [freelance deck v1](../projects/2026-09-11_freelance-deck-v1.md), [channel communication plan](2026-09-11_freelance-channel-communication-plan.md), [structure & dedup spec](../projects/2026-09-11_problem-structure-dedup-spec.md), [90-day plan](2026-09-11_launch-plan-90-days.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- `skills/*/SKILL.md` on disk, before and after the edits of 2026-09-11

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
