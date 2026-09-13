---
last_reviewed: 2026-09-13
---

# Domain name shortlist — Ouch! / FixMyLife

> One-line TL;DR: `cacoince.fr` is the recommended buy (≈5–8 € HT/year at OVHcloud, 1 € first year at Ionos); `aiemavie.fr` and `fixmavie.fr` are the two alternates. All three are free on every checked extension, so the brand can be locked cheaply.

| Field | Value |
|---|---|
| **Date** | 2026-09-13 |
| **Type** | strategy |
| **Participants** | Fabien (founder), Claude (research) |
| **Source(s)** | DNS delegation checks (Google/Cloudflare resolvers), web search on 2026 registrar prices |

---

## Context

The app's public name is "Ouch!" (alias "FixMyLife", Lovable id `fix-it-karma`). `ouch.fr` is parked on dan.com (for sale, premium price) and `ouch.com/.app/.io/.co/.eu` are all taken. `fixmylife.com` is a live Loopia-hosted site; `fixmylife.fr` is free but would sit next to that brand. The goal was a domain that expresses the concept, sounds French and playful (victim register), stays neutral toward named entities, and costs a few euros.

## Method and its limit

- Availability was inferred from **DNS delegation** (no NS record at the registry = no delegation). WHOIS/RDAP endpoints are not reachable from the research environment. A `.fr` registered but never delegated would wrongly show as free, so **confirm in the registrar's search box before paying**.
- 130 names tested on `.fr` and `.com`; the 20 best also on `.app .co .xyz .io .net .ovh .eu .org .life .me`.

## Recommendation

**Buy `cacoince.fr`** ("ça coince").

- Names the product object exactly: a lived friction point, without judging the entity — the same line as the legal grid ("j'attends mon remboursement depuis 3 semaines" = ça coince).
- Works on both sides: victim CTA "Où ça coince ? Swipe." / maker pitch "Là où ça coince, il y a un marché."
- 8 letters, no accent needed, one obvious spelling once heard.
- `cacoince.com`, `.app`, `.co`, `.io`, `.eu`, `.xyz`, `.ovh` were all free at check time; `ca-coince.fr` is free for a defensive redirect.
- No existing brand, app or company found under "ça coince" / "cacoince" (only a 1990s children's book by Pef).

## Alternates (both free on .fr, .com and all checked extensions)

| Domain | Why | Watch-out |
|---|---|---|
| `aiemavie.fr` | "Aïe, ma vie" = French fusion of Ouch! + FixMyLife; pure victim register, close to the VDM meme | "aie" without accent looks odd in a URL; `aie-ma-vie.fr` also free |
| `fixmavie.fr` (+ `.com` free) | Direct French of FixMyLife, keeps brand continuity with the alias | Anglicism; less playful than the two above |

Other free and coherent options, lower priority: `jaiceprobleme.fr` (the literal swipe copy, long), `magalere.fr` / `mesgaleres.fr` (freelance vocabulary, generic), `ouchmoi.fr`, `heyouch.fr`, `ouch-app.fr`, `ouchapp.fr` (keep the "Ouch!" name, weaker on their own), `galerometre.fr` / `douleurometre.fr` (maker register), `scoredouleur.fr` (the metric, not consumer-facing).

Taken, for the record: `ouch.fr/.com`, `aie.fr/.com`, `ouille.fr/.com`, `capique.fr/.com`, `cacoince` none, `galere.fr/.com`, `moiaussi.com`, `fixmylife.com/.app/.co/.org`, `painscore.com`, `problemo.fr/.com`, `relou.fr/.com`, `grr.fr`.

## Price (2026, .fr)

| Registrar | Year 1 | Renewal | Note |
|---|---|---|---|
| OVHcloud | ≈ 5–7 € HT | ≈ 7 € HT | Stable price, no jump |
| Ionos | 1 € (sometimes free) | ≈ 11 € | Cheapest entry, most expensive renewal |
| Afnic wholesale reference | 5.07 € | — | Floor price any registrar pays |

`.com` ≈ 9 € year 1 / 13 € renewal at OVHcloud. `.xyz` ≈ 2 € year 1 but ≈ 14 € renewal. `.fr` requires an EU address (fine for a French founder).

## Next steps

1. Type `cacoince.fr` in OVHcloud's or Ionos' search box to confirm (DNS check is not registry-level).
2. Buy `cacoince.fr`; optionally `cacoince.com` (≈ 9 €) and `ca-coince.fr` as redirects. Total under 25 €.
3. Quick INPI trademark search on "ça coince" before printing anything.
4. Point the domain at the Vercel deployment once configured (see [`docs/deploy.md`](https://github.com/xeonfab/fix-it-karma/blob/main/docs/deploy.md)).

---

## Related pages
- [MOC Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)
- [Freelance channel communication plan](2026-09-11_freelance-channel-communication-plan.md) — the URL to share once the domain is live
