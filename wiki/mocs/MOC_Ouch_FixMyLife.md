---
last_reviewed: 2026-09-13
---

# 🗺️ MOC: Ouch! / FixMyLife

> Fabien's side project (Lovable project `fix-it-karma`, public name "Ouch!"/"FixMyLife"): a two-sided platform where victims swipe daily-life frustrations and makers mine the resulting Score de Douleur for validated market opportunities.

---

## 🧠 Core concepts
- [Score de Douleur](../concepts/Score_de_Douleur.md) — the pain-ranking formula that is the whole product thesis
- [Resolution Type A/B](../concepts/Resolution_Type_AB.md) — tiers-fixable vs entity-only, drives the public disclaimer

## 👥 Key entities
<!-- No people/org entity pages yet for this project — the 13-16 named real-world entities (SNCF, Doctolib, Qonto, ...) are in-product content, not wiki entities. Add a wiki entity page here only if a real maker/partner relationship starts (e.g. an investor, a co-founder). -->

## 📚 Syntheses & strategy
- [Community-by-community rollout playbook](../syntheses/strategy/2026-09-11_community-rollout-playbook.md) — **the long-run shape**: ship → one community → map its channels → test problem submission → store/structure → offer to makers → automate → replay on the next community; the 90-day plan is iteration #1
- [90-day launch plan (CEO)](../syntheses/strategy/2026-09-11_launch-plan-90-days.md) — **the active plan**: audit of the real build state, 6 settled decisions, 3 phases with hard gates, weekly rhythm, metrics, kill criteria
- [Ouch!/FixMyLife — full project context](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md) — concept, business model, hard rules, data model, build status, next steps
- [Test de concept — communauté freelances](../syntheses/strategy/2026-09-10_test-concept-communaute-freelances.md) — message + structure de landing page pour le test de validation publique, jamais exécuté jusqu'ici
- [Dépôt d'un problème — décision du panel double-face](../syntheses/strategy/2026-09-11_depot-probleme-panel-decision.md) — refonte du flow de dépôt, scope resserré au partage social après découverte que le reste du brief était déjà construit

## 🧾 Freelance push — Cercle 1 workstreams (2026-09-11)
- [Freelance deck v1](../syntheses/projects/2026-09-11_freelance-deck-v1.md) — **content**: card standard, 54 cards (8 existing kept/rewritten, 46 new), 10-card launch deck, insertion procedure
- [Freelance channel communication plan](../syntheses/strategy/2026-09-11_freelance-channel-communication-plan.md) — **distribution**: per-channel playbook and copy, harvest protocol, proxy submission, metrics by channel
- [Problem structure & dedup spec](../syntheses/projects/2026-09-11_problem-structure-dedup-spec.md) — **platform**: community tag, real-entities-only registry (retire 18 placeholders), 3-layer dedup with canonical merge, presentation rules

## 🧑‍🤝‍🧑 Team
- [Channel tracking](../syntheses/research/channel-tracking.md) — **measurement**: `channel_funnel` / `channel_weekly` / `channel_problems` / `launch_kpis` views, weekly sheet, anomalies to fix before the LinkedIn wave
- [Team skills audit & upgrade](../syntheses/strategy/2026-09-11_team-skills-audit.md) — twelve seats, who leads which workstream, what was fixed (auto-trigger defect, obsolete CTO/CEO context) and created (`ouch-expert-independants`, `ouch-editeur-cartes`, `ouch-data-analyst`)

## 🚦 Build state delta (2026-09-11 live audit vs 2026-09-10 snapshot)
- Persistence is **still `localStorage` only** (`src/lib/engagement.tsx`); Supabase holds only a `profiles` table for Google SSO. Shared persistence is Phase 1 of the launch plan and a hard prerequisite before any external share.
- New since the snapshot: `/communaute/independants` + `/catalogue` (Cercle 1 landing with a 2-question survey, answers also `localStorage`), Google SSO offered after a positive swipe, social share after publishing a problem, duplicate detection on submission.
- Lovable `roadmap.md`: all 12 items checked. Feature backlog is empty by design (feature freeze, decision D5).
- The catalog ships demo counters and fake statuses; they are zeroed at migration (spec §1b).
- **2026-09-11 evening**: `main` of `fix-it-karma` does not typecheck (the persistence merge mangled `swipe-deck.tsx`'s flip card); repaired on branch `claude/freelance-deck-structure`, which also carries the Cercle 1 structure (communities tag, channel, deck_rank, banned-word check, trigram similarity, funnel events) and the freelance deck. Database already migrated: 84 cards, 82 published (F20/F22 wait for their source), only real entities linked.
- **Lovable exit, 2026-09-11 (settled in the app repo, `docs/deploy.md`)**: `main` now builds with a standard Vite/Nitro config targeting **Vercel**, Google sign-in via native Supabase auth, qualification and duplicate detection on the **Claude API** (`claude-opus-5`), npm lockfile, database = the founder's own Supabase project `ouch` (`mywbvjaitfqclenrvsdn`, Paris). Both PRs (#2 Lovable exit, #3 freelance deck + structure) are merged on `main` (`ad33d7d`). **Until Vercel is configured by Fabien** (30 min: Anthropic key, Google OAuth, env vars), no public URL serves the new build: `fix-it-karma.lovable.app` still shows the old build on the old Lovable Cloud database (38 seed cards, none of the new columns). Do not share any link before the Vercel deployment and the two-device test.
- Code lives in [`xeonfab/fix-it-karma`](https://github.com/xeonfab/fix-it-karma). Phase 1 spec: [`docs/persistence-spec.md`](https://github.com/xeonfab/fix-it-karma/blob/main/docs/persistence-spec.md); deployment: [`docs/deploy.md`](https://github.com/xeonfab/fix-it-karma/blob/main/docs/deploy.md).

## ❓ Open questions
- ~~Is the Supabase migration a prerequisite for the public validation test?~~ **Settled 2026-09-11 (D1): yes**, minimal schema, two-week cap — see launch plan.
- ~~Will "signer/signatures" be adopted before launch?~~ **Settled 2026-09-11 (D2): "concerné(e)s" is final for launch**; "signer" parked until ≥1,000 positive swipes.
- When does the Cercle 1 → Cercle 2 (PME) traction signal trigger? Unchanged (3 freelance problems >70 + 1 returning maker); it is the Phase 3 exit gate, evaluated at day 90 (week of 4 Dec 2026).
- ~~What are the "organisations able to collect problems" in the founder's strategy?~~ **Settled 2026-09-11: the product's entités.** Every problem tied to an entity must appear on that entity's public page; makers are either intrapreneurs inside the entity (Type B) or independents/collectives (Type A). Hard rules 4–5 unchanged. See the [rollout playbook](../syntheses/strategy/2026-09-11_community-rollout-playbook.md).
- Retire the 18 placeholder entities (their pages disappear) and `collectivite-locale` with them? Default yes — see the [dedup spec](../syntheses/projects/2026-09-11_problem-structure-dedup-spec.md).
- Anonymous publication if the Google login wall loses >50 % of submitters? Measure first (four funnel events), CEO decision after — see the [channel plan](../syntheses/strategy/2026-09-11_freelance-channel-communication-plan.md).
- Anonymous voter identity: device id only, or upgraded to the Google profile on sign-in? (Spec week, default = device id + link on sign-in.)

## 📥 Raw sources worth re-reading
- [raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md](../../raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md) — the authoritative full context dump

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-10 ouch-fixmylife-contexte-complet](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- [2026-09-10 test-concept-communaute-freelances](../syntheses/strategy/2026-09-10_test-concept-communaute-freelances.md)
- [2026-09-11 community-rollout-playbook](../syntheses/strategy/2026-09-11_community-rollout-playbook.md)
- [2026-09-11 depot-probleme-panel-decision](../syntheses/strategy/2026-09-11_depot-probleme-panel-decision.md)
- [2026-09-11 freelance-channel-communication-plan](../syntheses/strategy/2026-09-11_freelance-channel-communication-plan.md)
- [2026-09-11 freelance-deck-v1](../syntheses/projects/2026-09-11_freelance-deck-v1.md)
- [2026-09-11 launch-plan-90-days](../syntheses/strategy/2026-09-11_launch-plan-90-days.md)
- [2026-09-11 problem-structure-dedup-spec](../syntheses/projects/2026-09-11_problem-structure-dedup-spec.md)
- [2026-09-11 team-skills-audit](../syntheses/strategy/2026-09-11_team-skills-audit.md)
- [channel-tracking](../syntheses/research/channel-tracking.md)

**Other**

- [📇 Wiki Index](../index.md)

<!-- BACKLINKS:END -->
