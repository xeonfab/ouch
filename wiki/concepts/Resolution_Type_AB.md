---
last_reviewed: 2026-09-10
---

# Resolution Type A/B

> One-line TL;DR: the `resolutionType` field ("tiers" vs "entite") that determines whether a problem can be fixed by an outside maker or only by the named entity — and which disclaimer is shown.

## What it is

- **Type A "tiers"**: bypassable by an external maker without the entity (e.g. SNCF Connect refund, Doctolib cancelled appointment).
- **Type B "entite"**: unsolvable without the entity itself (e.g. Qonto blocked account, France Travail login bug).
- Badges in clear language: "🛠️ Une solution externe est possible" (Type A) vs "🔒 Seule l'entité concernée peut résoudre ça" (Type B).
- Drives the public-communication disclaimer, which must differ by type — a single blanket statement for the whole catalog was explicitly rejected.

## Why it matters for Ouch!/FixMyLife

This distinction is what let the "pétition" vocabulary ("signer"/"signatures") stay under consideration without being dishonest: an honest disclaimer about who actually resolves the problem can't be a single sentence once Type A and Type B coexist in the catalog. As of the last session, "signer/signatures" was never actually shipped to Lovable — the app still says "concerné(e)s".

## Current status

- 🟢 Live / in production — field exists, badges are shown in detail views.
- 🔄 In progress: retroactive Type A/B qualification of the full existing catalog (sent to Lovable, status to verify on resume).

## Related concepts

- [Score de Douleur](Score_de_Douleur.md) — the ranking metric this badge sits alongside.

## Related entities

_(none yet)_

## Sources

- `raw/specs/2026-09-10_ouch-fixmylife-contexte-complet.md`

---

<!-- BACKLINKS:START -->
## Referenced by

**Concepts**

- [Score de Douleur](Score_de_Douleur.md)

**Syntheses**

- [2026-09-10 ouch-fixmylife-contexte-complet](../syntheses/projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- [2026-09-11 launch-plan-90-days](../syntheses/strategy/2026-09-11_launch-plan-90-days.md)

**Other**

- [📇 Wiki Index](../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
