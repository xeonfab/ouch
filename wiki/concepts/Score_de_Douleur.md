---
last_reviewed: 2026-09-10
---

# Score de Douleur

> One-line TL;DR: the pain-score formula that ranks problems in the Terminal Maker, letting a maker find an already-validated market before building anything.

## What it is

Weighted score computed per problem: **45% volume of positive swipes + 35% conversion rate + 20% opt-in emails collected**. It's the single sorting/filtering key on the Terminal Maker dashboard.

## Why it matters for Ouch!/FixMyLife

It's the core mechanism turning raw swipe data into a maker-facing signal — the whole product thesis is that a maker can trust this number instead of guessing demand. It also gates the launch-stage traction signal: moving from Cercle 1 (freelances) to Cercle 2 (PME) requires 3 freelance problems with a Score de Douleur >70 **and** at least one returning maker.

## Current status

- 🟢 Live / in production — computed and shown in the Terminal Maker.
- 🔴 Not supported: AI-suggested business ideas clustering multiple high-score problems (reserved for v2 Pro, deliberately not built — too risky to show before real data volume).

## Related concepts

- [Resolution Type A/B](Resolution_Type_AB.md) — the disclaimer shown alongside a scored problem depends on this field.

## Related entities

_(none yet — no external vendor/expert tied to this mechanism)_

## Sources

- `raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md`

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [Resolution Type AB](Resolution_Type_AB.md)

**Syntheses**

- [2026-09-10 ouch-fixmylife-contexte-complet](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- [2026-09-11 community-rollout-playbook](../syntheses/strategy/2026-09-11_community-rollout-playbook.md)
- [2026-09-11 launch-plan-90-days](../syntheses/strategy/2026-09-11_launch-plan-90-days.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
