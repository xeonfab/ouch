---
last_reviewed: 2026-09-12
---

# Problem structure & dedup spec — presenting problems cleanly, storing them without duplicates or fuzz

> One-line TL;DR: audit of how problems are stored and shown today (hard-coded community deck, 18 placeholder entities, duplicate check limited to one topic, no hashtags on seeds, no way to merge), then the minimal changes that make the freelance push clean: a `communities` tag, a real-entities-only registry, a three-layer dedup (SQL similarity → LLM judge across topics → human merge into a canonical card, never a deletion), a machine-checkable card standard, and presentation rules for the community page and entity pages. Sequenced against the feature freeze.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | project |
| **Participants** | Fabien (founder), `ouch-cto` (Marc), `ouch-ux-designer`, `ouch-legal` |
| **Source(s)** | Live read of `xeonfab/fix-it-karma` on 2026-09-11 and of the Lovable Cloud database schema (`problems`, `votes`, `leads`, `voices`, `confirmation_votes`, `survey_answers`, `events`, views); [persistence spec](https://github.com/xeonfab/fix-it-karma/blob/main/docs/persistence-spec.md) |

---

## Context

Workstream 3 of the freelance push: "continue the platform design so problems are well presented and well structured in the database, with no duplicates and no fuzzy elements". Phase 1 shipped the shared store. This spec covers what sits on top: how a problem is tagged, linked to an entity, deduplicated, and shown on the community page and the entity page. It respects D5 (feature freeze): each change is classified as *now* (instrumentation, legal-required data fix, bug-level), *Phase 2* (small, needed for the waves), or *after day 90*.

## 1. Audit — what the live code does today

| Area | Today | Problem |
|---|---|---|
| Community deck | `FREELANCE_PROBLEM_IDS = [1, 3, 9, 10, 13, 29, 34, 36, 37, 38]` hard-coded in `communaute.independants.index.tsx` | A freelance who submits a problem never sees it on the freelance page; every deck change is a deploy; four of the ten cards are not freelance-specific (see deck audit) |
| Entities | 31 entries in `entities.ts`; **18 are placeholders** (`dnum`, `ville-pilote`, `operateur-ferroviaire`, `mutuelle`, `editeur-crm`, `cabinet-comptable`, `cooperative-soignants`, `reseau-artisans`, `reseau-commercants`, `federation-batiment`, `federation-automobile`, `association-consommateurs`, `association-locataires`, `association-aidants`, `association-usagers`, `operateur-telecom`, `banque-pro-en-ligne`, `marketplace-ecommerce`); 13 are real (SNCF Connect, Doctolib, France Travail, URSSAF, Colissimo, impots.gouv, CAF, Mon Compte Formation, ARS, Collectivité locale, Qonto, Malt, Stripe) | Placeholders produce entity pages for organisations that do not exist; they contradict the founder's rule (an entity is a public name) and blur the maker signal. 24 of the 38 seed cards link to at least one placeholder |
| Taxonomy | 5 sectors × 3–4 topics, closed enums in `problems.ts`, mirrored in the `qualifyProblem` JSON schema | No place for the freelance-specific frictions (payment terms, social protection, status); they scatter across Fintech/Facturation, B2B/Ventes, B2B/Finance-Compta, Lifestyle/Vie administrative. Acceptable for launch (D-rule: no new filters before day 90) but the community tag must not depend on topics |
| `topic_hashtag` | `null` on all 38 seed rows; generated only for user submissions; client falls back to `#SectorTopic` | Seeds show generic hashtags; no context signal for makers |
| Duplicate detection | `detectDuplicate`: LLM judge over the **40 most recent published problems of the same sector and topic**, threshold 0.7, called once after qualification | Misses duplicates classified under another topic (the most common case: « relances » lands in Facturation or Ventes depending on wording); misses everything beyond 40 rows; no check at seed time; no post-hoc tooling |
| Merge / canonical | none; the only user-side path is « je rejoins cette carte » before publishing | Once two duplicates are published, nothing can regroup them; deletion is forbidden by product rule |
| Concreteness | enforced by prompt only (title must carry one concrete element) | Nothing server-side or in moderation checks it; seed title of id 1 does not even match its statement |
| Submission | requires Google login (`problems_insert_authenticated`), `source = 'user'`, no community tag, no channel tag on the row | Cannot attribute a submitted problem to a community or a channel; the login wall is unmeasured |
| Entity page | `/entite/:slug` lists `problemsForEntity(problems, slug)` | Fine functionally; presentation rules below |
| Events | six events with `props.utm` from `?c=` | No submission-funnel events |

## 2. Card standard — the single source of truth

The eight checks of the [deck page](2026-09-11_freelance-deck-v1.md#1-card-standard-definition-of-done) are the standard. Three of them become machine checks:

| Check | Where | Rule |
|---|---|---|
| Concrete element in title | moderation SQL (weekly) + `qualifyProblem` prompt (already) | flag titles with no digit and none of the markers `chaque`, `par semaine`, `par mois`, `par jour`, `par trimestre`, `heure`, `jour`, `semaine`, `mois`, `€`, `%` |
| No banned word | DB `check` constraint on `statement` and `title` (case-insensitive regex on the banned list) | insert refused; the prompt already rewrites, this is the safety net for seeds and scripts |
| Hashtag never names an entity | moderation SQL | flag hashtags containing any entity `name` from the registry |

## 3. Data model changes (minimal, all additive, no deletion)

```sql
-- 3.1 Community tag: which community decks a problem belongs to (a problem may belong to several)
alter table public.problems add column communities text[] not null default '{}';
create index on public.problems using gin (communities);

-- 3.2 Channel attribution of user submissions (copied from the session's ?c= at insert)
alter table public.problems add column channel text;

-- 3.3 Canonical merge: a duplicate stays visible but points to its canonical card; never deleted
alter table public.problems add column merged_into bigint references public.problems(id);
create index on public.problems (merged_into) where merged_into is not null;

-- 3.4 Similarity layer
create extension if not exists pg_trgm;
alter table public.problems add column norm_text text
  generated always as (lower(unaccent(coalesce(title,'') || ' ' || coalesce(statement,'')))) stored;
create index on public.problems using gin (norm_text gin_trgm_ops);

-- 3.5 Banned-word safety net (list mirrors the qualify prompt)
alter table public.problems add constraint problems_no_judgment check (
  statement !~* '(malhonn|arnaqu|escroqu|voleur|\mnul(le)?\M|inacceptable|scandaleu|incompétent|incompetent)'
  and title !~* '(malhonn|arnaqu|escroqu|voleur|\mnul(le)?\M|inacceptable|scandaleu|incompétent|incompetent)'
);
```

`unaccent` needs `create extension if not exists unaccent`. `problem_stats` gains one rule: counts are aggregated on `coalesce(merged_into, id)` so a merged card's votes and leads count for the canonical card; the merged row itself shows « regroupée avec » and links to the canonical one. Leads are never moved (consent is per problem; the maker export joins on the canonical id).

## 4. Taxonomy — communities are tags, topics stay as they are

- **Community** = who the card is for (`independants`, later `pme`, `citoyens`). Assigned at seed for curated cards; for user submissions, set from the page where the submission happened (`/communaute/:slug` → that community) or inferred by `qualifyProblem` with a new `communities` output (strict enum), confirmed in the preview as a chip. The community page filters on the tag, so a freelance's own card shows up on the freelance deck without a deploy.
- **Sector · Topic** = what the card is about (unchanged, no new filter before day 90). Proposed **v2 topics** to open when Cercle 2 starts, recorded here so the freelance cards can be re-tagged in one pass: Fintech → « Se faire payer », « Trésorerie & banque »; B2B → « Devis & contrats », « Statut & cotisations », « Protection sociale ». Until then, the mapping in the deck table applies.
- **Hashtag** = the concrete context, one per card, never an entity. Backfill the 38 seeds by hand (deck page gives the freelance ones).

## 5. Entity registry — real, public organisations only

Rules (from the founder's 2026-09-11 clarification and the legal grid):
1. An entity is a **real organisation with a public name** (company, public body, local authority, platform). Never a person; never a category (« une banque en ligne »); never a placeholder.
2. The registry stays in code (`entities.ts`) with a **closed list**; new entities enter only through a manual queue after a legal look (is the name public, is the friction attributable, is there a source).
3. Each entry carries `aliases` for matching voice-to-text and typos (« compteux », « q o n t o » → `qonto`), used by `qualifyProblem` and by the harvest step.
4. An entity page is created **only when at least one published card links to it** (already the behaviour of `usedEntities`).
5. An entity may become a maker; it never gets a badge, a reply, or a moderation right (hard rules 4–5, legal skill).

Actions on the current registry:
- **Retire the 18 placeholders**: set `entity_slugs = '{}'` on the 24 seed rows that reference them (their friction stands without the fake entity), then remove the entries from `entities.ts`. Entity pages for placeholders disappear, which is the intent. This is a legal/consistency data fix, allowed now.
- **Keep the 13 real entities.** `collectivite-locale` is a category, not an organisation; keep it only until a real local authority is named on a card, then retire it too.
- **Add on demand** from the harvest: the first candidates from the freelance channels will be banks, platforms and public bodies actually named in complaints (source logged).

## 6. Dedup — three layers, no deletion

| Layer | When | How | Outcome |
|---|---|---|---|
| **L1 — SQL similarity** | on every submission, on every seed insert, in the weekly moderation query | `similarity(norm_text, :candidate) > 0.45` over **all** published problems (not one topic), top 8 | candidate list, cheap, no LLM |
| **L2 — LLM judge** | on submission, on the L1 candidates only | existing `detectDuplicate` prompt (same friction = same situation + same blocker), threshold 0.7 | « quelqu'un a déjà signalé ça » screen, join instead of create (already built) |
| **L3 — human merge** | weekly, from the moderation query listing published pairs with L1 > 0.4 | Fabien decides: distinct / merge; merge sets `merged_into` on the newer card | one canonical card carries the counters; the duplicate stays readable and redirects |

Changes to `detectDuplicate`: replace the `sector`/`topic` filter with an L1 query (`order by similarity desc limit 8`), keep the LLM judge. That is a bug-level fix (duplicates across topics slip through today), allowed now.

Seed-time discipline: the 54-card deck was deduplicated by hand; the L1 query runs once more over the whole table before the deck is published (expected: no pair above 0.6).

Moderation query (weekly, `docs/metrics.sql`):

```sql
select a.id, b.id, round(similarity(a.norm_text, b.norm_text)::numeric, 2) as sim, a.title, b.title
from problems a join problems b on a.id < b.id
where a.published and b.published and a.merged_into is null and b.merged_into is null
  and similarity(a.norm_text, b.norm_text) > 0.4
order by sim desc;
```

## 7. Presentation rules

### Community page (`/communaute/:slug`)
- Deck = problems tagged with the community, not `verifying`/`resolved`, not merged, ranked by Score de Douleur then recency, **capped at 10** in the swipe; the rest in the ranked listing below (already built). Newly submitted cards (0 votes) get one guaranteed slot in the swipe for 48 hours so the submitter sees their card in circulation.
- One action above the fold: swipe. The « Ajoute-la » block moves below the deck (see the channel plan).
- Registers: fun on this page; no Terminal styling.
- Victim-side cards (listing and home): **one number per card, the one the visitor can move**. The vote is a visible button (« Moi aussi 🔥 », « Toi aussi ✓ » once voted), the count hidden at zero; the Score de Douleur `/100` never appears on these cards, it stays on the Terminal, the entity page and the duplicate screen of the submit flow (decided 2026-09-12 after Fabien's field review, PR #7).
- Card front and list row share the same landmarks (emoji, hashtag, entity, the « Moi aussi 🔥 » action); the card keeps the first-person statement (the hook), the row keeps the factual title (for scanning). No counter shown at zero anywhere on the victim side; the swipe screen shows only a « n / N » progress. Register « tu » on the whole victim side (PR #19).
- Two victim-side objects: the **card** for deciding (swipe, one at a time; the home « Tendances » showcase of six) and the **row** for reading (community listing, catalogue): rank, emoji, title, hashtag and entity, vote button in the right column, no sector chip, no topic label, no score (PR #11). The Terminal keeps its table.
- Every positive vote, on any surface (deck, list, home cards), is followed by the same opt-in path (PR #16, `LeadPromptProvider`): Google user or email already given → lead recorded silently; otherwise one Google / email prompt per visit. A vote surface without the opt-in is a lead leak.
- A vote is reversible by its author: the voted button retracts it (PR #12, `retract_vote` RPC keyed on the device uuid, trace in `events.vote_retracted`). Votes are not content; the no-deletion rule covers cards, voices and maker updates.
- A ranked list never re-sorts under the visitor's cursor: the order is computed once per page load and frozen for the visit, a card submitted during the visit goes first (PR #8). Live re-ranking is for the Terminal only.
- Author name: never above the write headline; stated once under the publish button (« Signée X · ce nom apparaît sur la carte »), because the name is public on the card.

### Entity page (`/entite/:slug`)
- Header = the capturable number: « N freelances / personnes concernées » summed over the entity's canonical cards; below it the cards ranked by Score de Douleur, grouped by topic when more than six.
- Every card links back to its swipe; the page never shows a rating, a ranking against other entities, or a reply box (legal grid).
- Cards merged into a canonical one do not appear twice.
- Page exists only when at least one published card is linked; placeholder entities are gone.

### Terminal Maker
- Unchanged register (factual, dark). Counts read on canonical ids. A `communities` filter is added to the sidebar only when the second community exists.

## 8. Submission flow — what changes and what does not

- **Now (instrumentation)**: events `submit_started`, `submit_preview`, `submit_login_wall` (preview shown to an anonymous visitor), `submit_published`; `channel` copied on the row.
- **Now (bug-level)**: L1 before L2 in `detectDuplicate`; community tag from the page context.
- **Unchanged until measured**: Google login to publish. If more than half of the visitors who reach the preview stop at the wall, the CEO decides on anonymous publication (device id, `published = false` until moderated). Not a Phase 2 default.
- **Unchanged**: the « je rejoins cette carte » path; the variants; the entity chip (which only offers real entities once placeholders are gone).

## 9. Sequencing against the plan

| Change | Class under D5 | When | Estimate |
|---|---|---|---|
| Submission-funnel events + `channel` column | instrumentation (D5-c) | with the deck insertion, ≤ 2026-10-01 | 2 h |
| Retire placeholder entities, unlink 24 rows | legal/consistency data fix (D5-b) | ≤ 2026-10-01, before any external share | 2 h |
| `communities` column + community page reads the tag | small, required by the waves (a submitted freelance card must appear on the freelance page) | ≤ 2026-10-01 | 3 h |
| Hashtag backfill on 38 seeds + 54-card insertion | content | ≤ 2026-10-01 | 3 h (deck page procedure) |
| `pg_trgm` + `norm_text` + L1 in `detectDuplicate` + weekly query | bug-level (duplicates slip through across topics) | Phase 2, week 4 | 3 h |
| Banned-word check constraint | safety net | with the migration above | 0.5 h |
| `merged_into` + stats on canonical + « regroupée avec » | needs UI on entity page, Terminal, swipe | Phase 2, week 6, only if the weekly query finds ≥3 real pairs; otherwise after day 90 | 5 h |
| Taxonomy v2 topics, `communities` filter in Terminal | new filters | after day 90, with Cercle 2 | — |
| Anonymous publication | product decision | only if the login wall is measured >50 % | — |

Total before the first wave: ~10 h, inside the Phase 1–2 build budget (8 h → 3 h per week).

## 10. Acceptance criteria

Status 2026-09-11: database side verified live (no placeholder slug left, all hashtags set, no published pair above 0.6 similarity, L1 function returns F01 for a paraphrase of it). Client side implemented on branch `claude/freelance-deck-structure`, to verify on the Lovable preview after merge.

- [ ] A problem submitted from `/communaute/independants` appears in that page's listing within one reload, with no deploy.
- [ ] No entity page exists for a placeholder; `select distinct unnest(entity_slugs) from problems` returns only real organisations.
- [ ] All published problems have a non-null `topic_hashtag` that contains no entity name.
- [ ] Submitting « je perds 3h par semaine à relancer mes factures » from the freelance page proposes card F01 as a duplicate even if the qualifier classifies it under B2B · Ventes.
- [ ] The weekly similarity query returns no published pair above 0.6 after the deck insertion.
- [ ] A seed insert containing « arnaque » is refused by the database.
- [ ] `events` shows the four submission-funnel events with `props.utm` set when `?c=` was present.

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Claude Code (`ouch-cto`) | Migration: `communities`, `channel`, banned-word check; unlink placeholders; events; community page on the tag | 2026-10-01 | **done 2026-09-11** (migrations `20260912090000_community_structure`, `20260912090100_freelance_deck_v1`, applied live) |
| Fabien | Confirm the retirement of the 18 placeholder entities (their pages disappear) | 2026-09-14 | open |
| Claude Code (`ouch-cto`) | `pg_trgm` layer + L1 in `detectDuplicate` + weekly query in `docs/metrics.sql` | 2026-10-08 | **done 2026-09-11** (same branch) |
| Fabien | Weekly: run the similarity query on Sunday, decide merges | from 2026-10-12 | open |

## Open questions

- `collectivite-locale`: retire now with the other placeholders, or keep as the only category entity until a real local authority is named? Default: retire; the founder's rule is a public name.
- Should `merged_into` redirect the URL of the merged card to the canonical one (SEO) or show both? Default: show the merged card with a banner and the canonical link; no redirect (no content ever disappears).

## Related wiki pages

- Syntheses: [freelance deck v1](2026-09-11_freelance-deck-v1.md), [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md), [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md), [rollout playbook](../strategy/2026-09-11_community-rollout-playbook.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Live read of `xeonfab/fix-it-karma` on 2026-09-11: `src/lib/qualify.functions.ts`, `src/lib/duplicate.functions.ts`, `src/lib/entities.ts`, `src/lib/problems.ts`, `src/components/ouch/submit-flow.tsx`, `src/routes/communaute.independants.index.tsx`, `docs/persistence-spec.md`
- Lovable Cloud database `ouch` (`mywbvjaitfqclenrvsdn`): table list with columns, 38 rows of `problems`
- [raw/transcripts/2026-09-11_strategie-entites-et-makers.md](../../../raw/transcripts/2026-09-11_strategie-entites-et-makers.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 freelance-channel-communication-plan](../strategy/2026-09-11_freelance-channel-communication-plan.md)
- [2026-09-11 freelance-deck-v1](2026-09-11_freelance-deck-v1.md)
- [2026-09-11 freelance-deck-v1 expert-review](2026-09-11_freelance-deck-v1_expert-review.md)
- [2026-09-11 team-skills-audit](../strategy/2026-09-11_team-skills-audit.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
