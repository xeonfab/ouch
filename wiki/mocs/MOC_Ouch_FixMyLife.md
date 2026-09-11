---
last_reviewed: 2026-09-11
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
- [90-day launch plan (CEO)](../syntheses/strategy/2026-09-11_launch-plan-90-days.md) — **the active plan**: audit of the real build state, 6 settled decisions, 3 phases with hard gates, weekly rhythm, metrics, kill criteria
- [Ouch!/FixMyLife — full project context](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md) — concept, business model, hard rules, data model, build status, next steps

## 🚦 Build state delta (2026-09-11 live audit vs 2026-09-10 snapshot)
- Persistence is **still `localStorage` only** (`src/lib/engagement.tsx`); Supabase holds only a `profiles` table for Google SSO. Shared persistence is Phase 1 of the launch plan and a hard prerequisite before any external share.
- New since the snapshot: `/communaute/independants` + `/catalogue` (Cercle 1 landing with a 2-question survey, answers also `localStorage`), Google SSO offered after a positive swipe, social share after publishing a problem, duplicate detection on submission.
- Lovable `roadmap.md`: all 12 items checked. Feature backlog is empty by design (feature freeze, decision D5).
- The catalog ships demo counters and fake statuses; they are zeroed at migration (spec §1b).
- Code lives in [`xeonfab/fix-it-karma`](https://github.com/xeonfab/fix-it-karma). **Off Lovable since 2026-09-11**: Supabase project `ouch` (`mywbvjaitfqclenrvsdn`, Paris) on Fabien's own account, Vercel hosting, Claude API for qualification/duplicates. Phase 1 spec: [`docs/persistence-spec.md`](https://github.com/xeonfab/fix-it-karma/blob/claude/persistence-spec/docs/persistence-spec.md); deployment: [`docs/deploy.md`](https://github.com/xeonfab/fix-it-karma/blob/claude/persistence-spec/docs/deploy.md).

## ❓ Open questions
- ~~Is the Supabase migration a prerequisite for the public validation test?~~ **Settled 2026-09-11 (D1): yes**, minimal schema, two-week cap — see launch plan.
- ~~Will "signer/signatures" be adopted before launch?~~ **Settled 2026-09-11 (D2): "concerné(e)s" is final for launch**; "signer" parked until ≥1,000 positive swipes.
- When does the Cercle 1 → Cercle 2 (PME) traction signal trigger? Unchanged (3 freelance problems >70 + 1 returning maker); it is the Phase 3 exit gate, evaluated at day 90 (week of 4 Dec 2026).
- Anonymous voter identity: device id only, or upgraded to the Google profile on sign-in? (Spec week, default = device id + link on sign-in.)

## 📥 Raw sources worth re-reading
- [raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md](../../raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md) — the authoritative full context dump

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-10 ouch-fixmylife-contexte-complet](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- [2026-09-11 launch-plan-90-days](../syntheses/strategy/2026-09-11_launch-plan-90-days.md)

**Other**

- [📇 Wiki Index](../index.md)

<!-- BACKLINKS:END -->
