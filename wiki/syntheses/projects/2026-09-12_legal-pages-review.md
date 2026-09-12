---
last_reviewed: 2026-09-12
---

# Legal pages review (mentions légales, confidentialité, CGU)

> `ouch-legal` pass on the three legal pages of `fix-it-karma` before the first external wave. Two facts only Fabien can supply; everything else is fixed in PR #13.

| Field | Value |
|---|---|
| **Date** | 2026-09-12 |
| **Type** | project |
| **Owner** | `ouch-legal`, decisions by Fabien |
| **Pages** | `/mentions-legales`, `/confidentialite`, `/cgu` (routes `src/routes/*.tsx`, dated 10 septembre 2026) |
| **Related** | [90-day launch plan](../strategy/2026-09-11_launch-plan-90-days.md) · [dedup spec](2026-09-11_problem-structure-dedup-spec.md) · [MOC](../../mocs/MOC_Ouch_FixMyLife.md) |

## What was right already

- The three hard rules are stated as user-facing rules: lived fact not judgment, no natural person named, entity names only as context, no reply thread, no resale of emails without renewed consent.
- Email purpose is limited and explicit; the public/private split (public cards and scores, private emails) is clear.
- Tone is plain French, no legalese theatre.

## Gaps found, fixed in PR #13

| # | Page | Gap | Fix |
|---|---|---|---|
| 1 | Mentions légales | Publisher is « l'équipe Ouch! », which is nobody. The LCEN (art. 6, III) requires either the publisher's identity or, for a natural person publishing non-professionally, the statement that the identity is held by the host. | Non-professional natural-person clause, identity held by the host. Fabien can swap in his name and address if he prefers. |
| 2 | Mentions légales | Host is « son prestataire d'hébergement web », not named. The LCEN requires the host's name and address. | Vercel Inc. named for the site, Supabase Inc. for the data (database in Paris, EU). |
| 3 | Confidentialité | The device identifier (random uuid in local storage, attached to votes and usage events) and the usage events (page, swipe, arrival channel `?c=`) are personal data under the GDPR and were not listed. | Listed, with the legal basis (legitimate interest, no third-party tracker, no advertising). |
| 4 | Confidentialité | Submitted text is sent to Anthropic (United States) for rewording and duplicate detection: a processor and a transfer outside the EU, undisclosed. | Disclosed: what is sent (the text, never the email), why, where, and the transfer safeguard (standard contractual clauses). |
| 5 | Confidentialité | No legal bases, no right to object, no CNIL complaint mention, retention vague for votes, events and Google profile. | Added: bases per data, full rights list, CNIL, retention per data type. |
| 6 | Confidentialité | Data location not stated. | Database and emails hosted in Paris (EU) by Supabase; the site served by Vercel with a copy of public content on its edge network. |
| 7 | CGU | « modifié ou retiré » reads as deletion; the product rule is no deletion, correction, merge into a canonical card or unpublication. | Reworded; merge of duplicates into a canonical card stated. |
| 8 | CGU | Nothing on vote retraction or on how named entities are treated (no special status, correction by request only). | Both stated in one sentence each. |
| 9 | All three | Dated 10 septembre 2026. | 12 septembre 2026. |

## Two facts only Fabien can supply (still placeholders)

1. **Contact address**: `contact@ouch.example` appears on all three pages. It must be a real mailbox that Fabien reads (a Gmail alias is fine) before any external wave. GDPR requests and takedown requests arrive there.
2. **Publisher identity choice**: keep the non-professional natural-person clause (no name on the site, identity held by Vercel through the account), or publish name and address. The clause is valid as long as the project stays non-commercial; the day pricing goes live (`ouch-cfo` timeline), the name, legal form and SIREN become mandatory.

## To verify once on the providers' own legal pages

The host addresses were written from memory of the providers' terms: Vercel Inc., 440 N Barranca Ave #4133, Covina, CA 91723, USA; Supabase Inc., 970 Toa Payoh North #07-04, Singapore 318992. Fabien or `ouch-legal` checks them against vercel.com/legal and supabase.com/terms before the first wave (the sandbox cannot reach those pages).

## Not done, on purpose

- No cookie banner: only local storage for preferences, votes and the device id, plus the login session cookie, all exempt from consent under the CNIL guidelines. Adding a banner would be wrong, not just useless.
- No « droit de réponse » mechanism for named entities on the site: the product rule is no reply thread. Correction requests go through the contact address; this is stated.
