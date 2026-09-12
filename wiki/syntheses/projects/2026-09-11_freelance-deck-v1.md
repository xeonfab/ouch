---
last_reviewed: 2026-09-11
---

# Freelance deck v1 — 54 problem cards for Cercle 1

> One-line TL;DR: the seed content for the freelance community — a card-writing standard, an audit of the 10 cards currently hard-coded on `/communaute/independants`, 54 cards (8 existing kept or rewritten, 46 new) written to the standard and checked against the legal grid, and a 10-card launch deck picked out of them. Card copy is in French because it is product copy; everything else is in English.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | project |
| **Participants** | Fabien (founder), `ouch-growth-hacker` (Yasmine, copy), `ouch-persona-victime` (Léa, 2-second test), `ouch-legal` (grid), `ouch-cto` (Marc, insertability) |
| **Source(s)** | Live read of `xeonfab/fix-it-karma` on 2026-09-11 (`src/lib/qualify.functions.ts`, `src/lib/entities.ts`, `src/lib/problems.ts`, `src/routes/communaute.independants.index.tsx`) and the 38 rows of `public.problems` on the Lovable Cloud database; [rollout playbook](../strategy/2026-09-11_community-rollout-playbook.md); [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md) |

---

## Context

Workstream 1 of the freelance push: "a maximum of really good problems, perfectly written, about freelances, collected from the channels". The plan calls for a 10-card deck for the community link and ~60 curated cards in the catalogue before any scraping (D6). This page delivers the standard, the cards, and the selection. The companion pages are the [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md) (how to collect more and convince freelances to submit) and the [structure & dedup spec](2026-09-11_problem-structure-dedup-spec.md) (how they are stored without duplicates or fuzz).

## 1. Card standard (definition of done)

A card is publishable only if all eight checks pass. This is the same rule the `qualifyProblem` prompt enforces on user submissions; writers and moderators apply it by hand.

| # | Check | Pass example | Fail example |
|---|---|---|---|
| 1 | **Lived fact, first person** — `statement` is one sentence a freelance could say out loud, 90–180 characters | « Ma facture de mars est toujours impayée à 45 jours » | « Les freelances souffrent des retards de paiement » |
| 2 | **One concrete element** — a number, frequency, duration, amount, profile or precise situation, in both `statement` and `title` | « trois heures chaque vendredi » | « beaucoup de temps » |
| 3 | **No value judgment on any entity** — no banned words (« arnaque », « malhonnête », « nul », « inacceptable », « vol », « scandaleux », « incompétent »…), no generalisation (« ils font toujours ») | « personne ne peut me dire quand je récupère mes fonds » | « leur support est nul » |
| 4 | **Entity = organisation, real and public, or none** — never a person; never a placeholder (« banque pro en ligne », « réseau d'artisans » are not entities) | `qonto`, `urssaf-auto-entrepreneur`, or empty | `banque-pro-en-ligne`, « mon comptable » |
| 5 | **Hashtag names the context, never an entity** | `#SeuilTVA`, `#Paiement60Jours` | `#Qonto`, `#ProspectionLinkedIn` |
| 6 | **Title in third person, 40–90 characters, descriptive** — what a maker reads in the Terminal | « Payés à 60 jours fin de mois, les freelances avancent trois mois de trésorerie » | « Problème de paiement » |
| 7 | **Not a duplicate** — no existing card describes the same friction (same situation + same blocker), even under another topic | — | two cards about chasing unpaid invoices |
| 8 | **Source trace for entity-named cards** — a public source (review, forum thread, official procedure) logged in the sourcing sheet before insertion; never published verbatim | Trustpilot review URL + date | « everyone knows » |

Léa's tie-breaker: if she needs more than two seconds to recognise herself, the card goes back to the writer.

## 2. Audit of the current 10-card deck (`FREELANCE_PROBLEM_IDS = [1, 3, 9, 10, 13, 29, 34, 36, 37, 38]`)

| id | Current card | Verdict | Why |
|---|---|---|---|
| 1 | Title « perdent 3h/semaine à relancer les factures impayées » / statement « réconcilier les factures de mes sous-traitants » | **Rewrite** (F01) | Title and statement describe two different frictions; the statement is about subcontractors, not a typical freelance |
| 3 | Résilier un abonnement par courrier | **Drop from deck** (keep in catalogue) | Consumer friction, not freelance-specific; linked to a placeholder entity |
| 9 | Abonnements oubliés | **Drop from deck** (keep in catalogue) | Generic personal-finance card; placeholder entity |
| 10 | Devis refait à la main | **Keep** (F10), unlink placeholder entity `reseau-artisans` | Strong card, wrong entity |
| 13 | Notes de frais de douze collègues | **Drop from deck** (keep in catalogue) | A PME card (Cercle 2), not a freelance one |
| 29 | Déclaration URSSAF bloquée le jour de l'échéance | **Keep** (F19) | Entity-named, factual, source to log |
| 34 | Compte pro long à ouvrir puis bloqué | **Rewrite** (F30), unlink `banque-pro-en-ligne` | Placeholder entity; overlaps with 36 on the blocking part, refocused on account opening |
| 36 | Compte Qonto bloqué pour contrôle de conformité | **Keep** (F28) | Entity-named, factual, source to log |
| 37 | Paiement Malt conditionné à la validation client | **Keep** (F05) | Entity-named, factual, source to log |
| 38 | Fonds Stripe gelés | **Keep** (F29) | Entity-named, factual, source to log |

Also in the catalogue and freelance-relevant: id 2 (CPF on mobile, not freelance-specific), id 31 (multi-source income tax return, entity `impots-gouv`, kept as F23).

## 3. The 54 cards

Columns: `Ref` = existing id or new · `Sector · Topic` uses the current taxonomy only (insertable today; the proposed freelance topics are in the spec) · `Type` = `tiers` (a third party can build around it) / `entite` (only the named entity can fix it) · `Harvest` = where this complaint is typically found, for the channel plan · `Legal` = grid verdict.

### A. Getting paid (Fintech · Facturation)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F01 | id 1 rewrite | Chaque vendredi, je perds trois heures à relancer mes factures impayées et à vérifier lesquelles sont enfin réglées. | Les indépendants perdent 3 h par semaine à relancer et pointer leurs factures impayées | Fintech · Facturation | — | tiers | #RelanceFacture | 📨 | LinkedIn, FB groups | OK |
| F02 | new | Je n'ose pas appliquer les pénalités de retard écrites sur mes factures, de peur de perdre le client pour la prochaine mission. | Les pénalités de retard prévues au contrat ne sont presque jamais réclamées par les indépendants | Fintech · Facturation | — | tiers | #PenalitesDeRetard | 😬 | FB groups, Slack collectives | OK |
| F03 | new | Mon client grand compte paie à 60 jours : j'ai livré début janvier, l'argent arrive fin mars, et j'ai payé mes cotisations entre-temps. | Payés à 60 jours, les freelances avancent deux mois de trésorerie aux grands comptes | Fintech · Facturation | — | tiers | #Paiement60Jours | 🗓️ | LinkedIn | OK |
| F04 | new | Pour être payé, je dois d'abord me faire référencer sur le portail fournisseur du client : douze documents et trois semaines avant d'envoyer ma première facture. | Le référencement fournisseur d'un grand compte prend trois semaines avant la première facture | Fintech · Facturation | — | tiers | #PortailFournisseur | 🗂️ | LinkedIn, Slack collectives | OK |
| F05 | id 37 keep | Sur Malt, je dois attendre que mon client valide ma mission pour être payé, et certains mettent des semaines sans que le support intervienne. | Paiement freelance conditionné à la validation client | B2B · Ventes | malt | tiers | #ValidationMission | ⏳ | Reddit, Trustpilot | OK — source to log |
| F06 | new | Un client a disparu après la livraison du site : plus de réponse aux mails, et 1 800 € de facture dans le vide. | Un client injoignable après livraison laisse un freelance avec 1 800 € impayés | Fintech · Facturation | — | tiers | #ClientFantome | 👻 | FB groups, Reddit | OK |
| F07 | new | Je n'ai pas demandé d'acompte sur un projet de deux mois, et le client a changé d'avis à mi-parcours : un mois de travail non payé. | Sans acompte, un changement d'avis client coûte un mois de travail à un freelance | Fintech · Facturation | — | tiers | #Acompte | 🫠 | FB groups | OK |
| F08 | new | Pour une facture de 300 €, monter un dossier d'injonction de payer me prendrait plus de temps que la facture ne m'en a demandé. | Sous 500 €, recouvrer un impayé coûte plus de temps qu'il n'en rapporte à un indépendant | Fintech · Facturation | — | tiers | #PetitImpaye | ⚖️ | Forums, Reddit | OK |
| F09 | new | Mes clients me paient par virement, chèque, PayPal et parfois en espèces : je passe une heure par semaine à pointer qui a payé quoi. | Rapprocher paiements et factures prend une heure par semaine aux freelances multi-moyens de paiement | Fintech · Facturation | — | tiers | #Rapprochement | 🧾 | FB groups | OK |

### B. Quotes, contracts, scope (B2B · Ventes)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F10 | id 10 keep | Je dois refaire mon devis à la main dès qu'un client demande une petite modification. | Devis et acomptes : tout est refait à la main à chaque modification | Fintech · Facturation | — (unlink `reseau-artisans`) | tiers | #DevisAMain | ✏️ | FB groups | OK |
| F11 | new | « Juste une petite modif » : sur mon dernier projet, j'ai compté onze petites modifs gratuites, soit deux jours de travail non facturés. | Onze « petites modifs » gratuites font deux jours non facturés sur un projet freelance | B2B · Ventes | — | tiers | #ScopeCreep | 🔁 | LinkedIn, Slack collectives | OK |
| F12 | new | J'ai démarré la mission sur un simple « ok pour moi » par mail, et le devis n'a jamais été signé : au moment de facturer, le client conteste le périmètre. | Un devis jamais signé laisse le freelance sans base pour facturer le périmètre convenu | B2B · Ventes | — | tiers | #DevisNonSigne | 📝 | FB groups, forums | OK |
| F13 | new | Je passe deux heures en réunion de cadrage, puis le client choisit quelqu'un d'autre : ce temps-là n'est jamais facturé. | Les réunions de cadrage non facturées coûtent plusieurs heures par prospect aux indépendants | B2B · Ventes | — | tiers | #CadrageGratuit | 🕑 | LinkedIn | OK |
| F14 | new | Je réponds à des appels d'offres de vingt pages pour des missions de 5 000 €, et une fois sur deux je n'ai même pas de réponse. | Répondre à un appel d'offres freelance : vingt pages, et une réponse une fois sur deux | B2B · Ventes | — | tiers | #AppelDOffres | 📄 | LinkedIn, Slack collectives | OK |
| F15 | new | Je ne sais jamais si mon TJM est dans la norme : les grilles que je trouve varient du simple au double pour le même métier. | Les freelances ne trouvent aucune référence fiable pour fixer leur TJM | B2B · Ventes | — | tiers | #TJM | 💶 | Reddit, FB groups, Slack | OK |
| F16 | new | Chaque client me renvoie ses propres conditions d'achat de trente pages à signer, et je ne sais pas ce que j'accepte sur la propriété de mon travail. | Signer les conditions d'achat de chaque client : trente pages et des droits cédés sans les comprendre | B2B · Ventes | — | tiers | #ConditionsDAchat | 📚 | Slack collectives, forums | OK |
| F17 | new | Mon client me demande un test technique de deux jours non payé avant de me confier une mission freelance. | Des tests techniques de deux jours non rémunérés avant une mission freelance | B2B · Ventes | — | tiers | #TestNonPaye | 🧪 | Reddit, LinkedIn | OK |

### C. Contributions, VAT, taxes (B2B · Finance/Compta)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F18 | new | J'ai dépassé le seuil de TVA en cours d'année sans m'en rendre compte : trois factures à refaire et de la TVA à reverser que je n'avais pas encaissée. | Le dépassement du seuil de TVA surprend les micro-entrepreneurs en cours d'année | B2B · Finance/Compta | — | tiers | #SeuilTVA | 📈 | FB groups, forums | OK |
| F19 | id 29 keep | Le jour de ma déclaration de chiffre d'affaires, le site est bloqué et je n'ai aucune alternative simple. | Déclaration de chiffre d'affaires bloquée le jour de l'échéance | B2B · Finance/Compta | urssaf-auto-entrepreneur | entite | #DeclarationCA | 🧱 | X, FB groups | OK — source to log |
| F20 | new | Je passe une soirée par trimestre à comprendre quelle case remplir sur ma déclaration quand j'ai des revenus mixtes prestations et ventes. | Déclarer des revenus mixtes prend une soirée par trimestre aux micro-entrepreneurs | B2B · Finance/Compta | urssaf-auto-entrepreneur | tiers | #DeclarationMixte | 🧩 | Forums | OK — source to log |
| F21 | new | Ma CFE est arrivée en décembre alors que je n'avais pas prévu cette dépense : 600 € à sortir juste avant les fêtes. | La CFE de décembre tombe sans avertissement sur la trésorerie des indépendants | B2B · Finance/Compta | — | tiers | #CFE | 🎄 | FB groups | OK |
| F22 | new | Je dois fournir une attestation de vigilance tous les six mois à chaque client, et la télécharger prend dix minutes à chaque fois parce que mon espace ne s'ouvre pas du premier coup. | L'attestation de vigilance redemandée tous les six mois coûte dix minutes par client et par contrat | B2B · Finance/Compta | urssaf-auto-entrepreneur | entite | #AttestationVigilance | 📎 | Forums | OK — source to log |
| F23 | id 31 keep | Je déclare des revenus de plusieurs natures et je passe des heures à vérifier que je n'ai rien oublié. | Déclaration de revenus multi-sources : des allers-retours entre rubriques | Lifestyle · Vie administrative | impots-gouv | entite | #DeclarationRevenus | 🧮 | Forums | OK — source to log |
| F24 | new | Pour passer de micro-entreprise à SASU, j'ai eu quatre interlocuteurs différents et je ne sais toujours pas quand ma micro est officiellement fermée. | Changer de statut micro → SASU laisse un indépendant sans date de clôture claire | Lifestyle · Vie administrative | — | tiers | #ChangementDeStatut | 🔀 | Forums, Reddit | OK |
| F25 | new | Facture électronique obligatoire : je reçois des mails de trois plateformes différentes et je ne sais pas laquelle choisir ni ce que ça change pour mes factures. | La réforme de la facture électronique laisse les indépendants choisir une plateforme sans repère | Fintech · Facturation | — | tiers | #FactureElectronique | 📧 | LinkedIn, FB groups | OK |
| F26 | new | Je mélange dépenses perso et pro sur la même carte, et chaque trimestre je passe un dimanche à trier 200 lignes de relevé. | Trier 200 lignes de relevé perso/pro coûte un dimanche par trimestre aux micro-entrepreneurs | Fintech · Budget | — | tiers | #ReleveBancaire | 🗃️ | FB groups | OK |
| F27 | new | Je paie 120 € par mois pour la saisie de quinze factures, sans conseil ni échange en dehors de la clôture annuelle. | 120 € par mois de comptabilité pour quinze factures, sans conseil hors clôture | B2B · Finance/Compta | — | tiers | #CoutComptable | 💸 | FB groups, Reddit | OK (fact about the service received, no named firm) |

### D. Bank, cash, financing (Fintech · Budget, B2B · Finance/Compta, Lifestyle · Logement)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F28 | id 36 keep | Mon compte Qonto a été bloqué pour un contrôle de conformité et personne ne peut me dire quand je récupère mes fonds. | Blocage de compte pro sans délai ni interlocuteur humain | Fintech · Budget | qonto | entite | #CompteBloque | 🔒 | Trustpilot, X, Reddit | OK — source to log |
| F29 | id 38 keep | Stripe a gelé mes fonds pour une « revue de risque » et les réponses du support sont des messages types qui ne font pas avancer mon dossier. | Fonds marchands gelés plusieurs semaines sans visibilité | Fintech · Paiements partagés | stripe | entite | #FondsGeles | 🧊 | Reddit, Indie Hackers | OK — source to log |
| F30 | id 34 rewrite | Il m'a fallu cinq semaines et trois envois des mêmes justificatifs pour ouvrir un compte pro en tant que micro-entrepreneur. | Ouvrir un compte pro en micro-entreprise : cinq semaines et trois envois de justificatifs | B2B · Finance/Compta | — (unlink `banque-pro-en-ligne`) | tiers | #OuvertureComptePro | 🏦 | FB groups, Reddit | OK |
| F31 | new | Ma banque a refusé mon prêt immobilier parce que je n'ai que deux bilans en freelance, alors que je gagne plus qu'en CDI. | Sans trois bilans, les freelances se voient refuser un prêt immobilier malgré leurs revenus | Lifestyle · Logement | — | tiers | #PretImmoFreelance | 🏠 | FB groups, Reddit | OK |
| F32 | new | Pour louer un appartement, j'ai dû fournir un garant à 38 ans parce que mon statut d'indépendant ne rassure pas les agences. | Louer un appartement en freelance impose un garant même avec des revenus stables | Lifestyle · Logement | — | tiers | #GarantLocation | 🔑 | FB groups, Reddit | OK |
| F33 | new | Je ne sais jamais combien mettre de côté pour les cotisations et l'impôt : je découvre le montant réel six mois après avoir dépensé l'argent. | Les freelances découvrent le montant réel de leurs charges six mois après | Fintech · Budget | — | tiers | #ProvisionCharges | 🫣 | FB groups, Slack | OK |
| F34 | new | Un mois à 8 000 € puis un mois à 0 € : je n'ai aucun outil qui lisse ma trésorerie et me dise ce que je peux vraiment me verser. | Des revenus irréguliers sans outil pour savoir ce qu'un freelance peut se verser chaque mois | Fintech · Budget | — | tiers | #RevenusIrreguliers | 🎢 | LinkedIn, Slack | OK |
| F35 | new | Depuis que je dépasse 10 000 € de chiffre d'affaires, il me faut un compte dédié : ma banque n'a accepté qu'un compte pro à 9 € par mois, dont je n'utilise que le virement. | Le compte dédié des micro-entrepreneurs devient un compte pro payant à 9 € par mois | Fintech · Budget | — | tiers | #CompteDedie | 💳 | FB groups | OK |

### E. Social protection, health (Santé · Prévention, Lifestyle)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F36 | new | En arrêt maladie une semaine, j'ai touché 90 € d'indemnités et perdu 1 500 € de facturation. | Une semaine d'arrêt maladie coûte 1 500 € de facturation à un freelance, contre 90 € d'indemnités | Santé · Prévention | — | tiers | #ArretMaladieFreelance | 🤒 | FB groups, LinkedIn | OK |
| F37 | new | Mon relevé de carrière affiche des trimestres manquants pour mes années en micro-entreprise, et je ne sais pas à qui demander la correction. | Des trimestres de retraite manquants pour les années en micro-entreprise, sans interlocuteur clair | Lifestyle · Vie administrative | — | entite | #RetraiteMicro | 🧓 | Forums | OK |
| F38 | new | Pour mon congé maternité en freelance, j'ai dû calculer moi-même mes indemnités entre trois simulateurs qui ne donnent pas le même résultat. | Le congé maternité des indépendantes : trois simulateurs, trois montants différents | Lifestyle · Famille | — | tiers | #CongeMaterniteFreelance | 🤰 | FB groups | OK |
| F39 | new | Je n'ai vu aucun médecin du travail depuis que je suis freelance, et je n'ai aucun rappel pour mes visites de prévention. | Aucune visite médicale de prévention depuis le passage en freelance | Santé · Prévention | — | tiers | #PreventionFreelance | 🩺 | LinkedIn | OK |
| F40 | new | Après cinq ans de freelance, j'ai arrêté mon activité et j'ai découvert que je n'avais droit à aucune allocation, faute de conditions que personne ne m'avait expliquées. | Un freelance qui arrête après cinq ans découvre qu'il n'a droit à aucune allocation | Lifestyle · Vie administrative | — | tiers | #ChomageIndependants | 🚪 | Reddit, forums | OK |
| F41 | new | Ma mutuelle me coûte 80 € par mois de ma poche, le double de ce que je payais en CDI avec la part employeur. | La mutuelle coûte deux fois plus cher aux freelances qu'aux salariés, sans participation employeur | Santé · Prévention | — | tiers | #MutuelleFreelance | 🛡️ | FB groups | OK |

### F. Platforms and prospecting (B2B · Ventes)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F42 | new | Sur les plateformes freelance, la commission prélevée sur ma mission atteint 10 à 20 %, et le client ne le voit même pas dans mon tarif. | Jusqu'à 20 % de commission sur les missions freelance, invisibles pour le client | B2B · Ventes | — | tiers | #CommissionPlateforme | 🪙 | Reddit, FB groups | OK (no platform named) |
| F43 | new | Une ESN me place chez son client à 650 € par jour et m'en reverse 400, sans que je puisse parler directement au client. | L'intermédiation prend 250 € par jour sur une mission freelance sans contact direct client | B2B · Ventes | — | tiers | #Intermediaire | 🧱 | LinkedIn, Reddit | OK |
| F44 | new | Je passe cinq heures par semaine à publier sur les réseaux pour trouver des clients, sans savoir si un seul contrat en est sorti. | Cinq heures de réseaux sociaux par semaine sans savoir si un contrat en découle | B2B · Ventes | — | tiers | #ProspectionReseaux | 📣 | LinkedIn | OK |
| F45 | new | Mes anciens clients me recommandent de bouche à oreille, mais je n'ai aucun endroit où afficher leurs avis en dehors des plateformes qui prennent une commission. | Les recommandations clients des freelances restent captives des plateformes à commission | B2B · Ventes | — | tiers | #AvisClients | ⭐ | Slack collectives | OK |
| F46 | new | Un client m'a proposé du portage salarial : 10 % de frais de gestion plus les charges, et je n'arrive pas à comparer avec ma micro. | Portage salarial ou micro-entreprise : impossible de comparer le net réel | B2B · Finance/Compta | — | tiers | #PortageSalarial | 🔍 | Forums, Reddit | OK |

### G. Admin and tools (B2B · Ops, Lifestyle · Vie administrative)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F47 | new | Je jongle entre quatre outils pour une seule facture : le devis dans l'un, la facture dans l'autre, le suivi dans un tableur et la relance par mail. | Quatre outils pour émettre et suivre une seule facture freelance | Fintech · Facturation | — | tiers | #OutilsFacturation | 🧰 | FB groups | OK |
| F48 | new | Je reçois trois appels par semaine pour « utiliser mon solde CPF », et je ne sais pas lesquels sont sérieux. | Trois appels par semaine de démarchage CPF non sollicité chez les indépendants | Lifestyle · Vie administrative | — | tiers | #DemarchageCPF | 📵 | FB groups, X | OK (no entity tagged) |
| F49 | new | Je perds une demi-journée par mois à retrouver les justificatifs que mon comptable me redemande, éparpillés entre mails, photos et téléchargements. | Une demi-journée par mois à retrouver des justificatifs éparpillés | B2B · Finance/Compta | — | tiers | #Justificatifs | 🔎 | FB groups | OK |
| F50 | new | Mon avis de situation m'est demandé à chaque nouveau client, et je dois le retélécharger à chaque fois parce qu'il doit dater de moins de trois mois. | Un avis de situation de moins de trois mois à re-télécharger pour chaque nouveau client | Lifestyle · Vie administrative | — | tiers | #AvisDeSituation | 📑 | Forums | OK |
| F51 | new | J'ai perdu une journée à comprendre comment facturer un client en Belgique : TVA intracommunautaire, numéro à vérifier, mention à ajouter. | Facturer un client dans l'UE coûte une journée de recherche à un freelance | Fintech · Facturation | — | tiers | #TVAIntracom | 🇪🇺 | Forums, Reddit | OK |
| F52 | new | Je facture aussi des clients hors UE, et chaque paiement reçu perd 3 à 4 % entre frais de change et frais bancaires. | Les paiements internationaux coûtent 3 à 4 % aux freelances à chaque virement | Fintech · Facturation | — | tiers | #PaiementInternational | 🌍 | Indie Hackers, Reddit | OK |

### H. Time and isolation (B2B · RH / Ops)

| # | Ref | Statement (swipe) | Title (Terminal) | Sector · Topic | Entity | Type | Hashtag | Emoji | Harvest | Legal |
|---|---|---|---|---|---|---|---|---|---|---|
| F53 | new | Je n'ai pris que six jours de vacances cette année parce que chaque jour off est un jour non facturé et je n'ai personne pour me remplacer. | Six jours de vacances par an : chaque jour off est un jour non facturé en freelance | B2B · RH | — | tiers | #VacancesFreelance | 🏖️ | LinkedIn, FB groups | OK |
| F54 | new | Je travaille seule depuis mon salon depuis trois ans, et le coworking le plus proche coûte 250 € par mois, soit ma marge de la semaine. | Un coworking à 250 € par mois équivaut à une semaine de marge pour une freelance isolée | B2B · Ops | — | tiers | #Isolement | 🛋️ | FB groups | OK |

Dedup pass done while writing: a first draft had a card « facture de mars impayée à 45 jours, trois relances » next to F01; same friction (chasing unpaid invoices), merged into F01. F30 was refocused on account *opening* so it no longer overlaps F28 (account *blocking*). F09 (reconciling payments) and F47 (tool sprawl) are kept apart: different blocker.

## 4. Launch deck — the 10 cards on `/communaute/independants`

Picked for Léa's two-second test, spread across the freelance week, at most one entity-named card so the first test measures the frictions, not the brands. Replaces `FREELANCE_PROBLEM_IDS` once inserted.

| Order | Card | Why it opens or closes the deck |
|---|---|---|
| 1 | F01 relances impayés | The one every freelance recognises; opens with a sure right swipe |
| 2 | F11 onze petites modifs | Funny, painfully precise |
| 3 | F03 60 jours fin de mois | Grands comptes; concrete calendar |
| 4 | F10 devis refait à la main | Existing card, proven |
| 5 | F18 seuil de TVA | Admin surprise, strong maker signal (Type A) |
| 6 | F33 combien mettre de côté | The silent monthly anxiety |
| 7 | F36 arrêt maladie 90 € | Emotional peak of the deck |
| 8 | F31 prêt immo refusé | Life outside work; wide identification |
| 9 | F28 Qonto bloqué | The single entity-named card; feeds the week-7 entity-page share test |
| 10 | F42 commissions plateformes | Closes on the maker-side opportunity |

Alternates if a card under-performs (<30 % right swipes after 50 votes): F05 Malt, F19 URSSAF, F07 acompte, F25 facture électronique.

## 5. Insertion procedure (CTO)

1. Log the public source for the seven entity-named cards (F05, F19, F20, F22, F23, F28, F29) in the sourcing sheet (URL, date, nature). No source, no insertion.
2. Insert the 46 new cards with `source = 'seed'`, `status = 'incubation'`, `published = true`, counters at zero; rewrite ids 1 and 34; unlink the placeholder entities on ids 10 and 34 (`entity_slugs = '{}'`).
3. Backfill `topic_hashtag` for the existing rows (currently `null` on all 38).
4. Tag the 54 cards with the community (`communities = '{independants}'` once the column exists, see the spec; until then update `FREELANCE_PROBLEM_IDS` with the 10 new ids).
5. Run the dedup query from the spec across the whole table before publishing; expected: zero pair above 0.6 similarity.

A CSV export of the 54 rows sits next to this page: [`2026-09-11_freelance-deck-v1.csv`](2026-09-11_freelance-deck-v1.csv).

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Read the 54 cards once as Léa; strike any that fails the two-second test | 2026-09-14 | open |
| `ouch-expert-independants` | Factual review of the 54 cards (mechanism, figures, entity, Type A/B, frequency) | 2026-09-17 | **done 2026-09-11** → [expert review](2026-09-11_freelance-deck-v1_expert-review.md); 4 cards corrected in place (F03, F08, F16, F35), 1 title tightened (F22) |
| Fabien + `ouch-legal` | Source trace for the seven entity-named cards | 2026-09-17 | **done 2026-09-12** → [sourcing sheet](../research/sourcing-sheet-entity-cards.md); F20 and F22 published |
| Claude Code (`ouch-cto`) | Insert the deck on `fix-it-karma` (seed script, hashtags, deck ids) after the Phase 1 two-device test | 2026-10-01 | **done 2026-09-11** — inserted live by migration; F20 and F22 unpublished until their source is logged (`update problems set published = true where topic_hashtag in ('#DeclarationMixte','#AttestationVigilance')`) |
| Fabien | Swap the launch deck on `/communaute/independants` to the 10 cards above | 2026-10-01 | **done** — the page now reads the `communities` tag and `deck_rank` (branch `claude/freelance-deck-structure`) |

## Open questions

- Should cards mentioning a public body without tagging it (F21 CFE, F37 retraite, F40 allocation) stay untagged? Default yes: the friction is about anticipation or information, not about one identified service, and the registry has no matching real entity yet.
- F43 (ESN intermediation) and F42 (platform commissions) are the two cards most likely to draw makers rather than freelances; keep them in the catalogue even if they swipe below 30 %.

## Related wiki pages

- Syntheses: [channel communication plan](../strategy/2026-09-11_freelance-channel-communication-plan.md), [structure & dedup spec](2026-09-11_problem-structure-dedup-spec.md), [90-day plan](../strategy/2026-09-11_launch-plan-90-days.md), [rollout playbook](../strategy/2026-09-11_community-rollout-playbook.md)
- Concepts: [Score de Douleur](../../concepts/Score_de_Douleur.md), [Resolution Type A/B](../../concepts/Resolution_Type_AB.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

## Sources

- Live read of `xeonfab/fix-it-karma` (Lovable project `08a02fd1…`) on 2026-09-11 and of the `problems` table (38 rows) on the Lovable Cloud database
- [raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md](../../../raw/transcripts/2026-09-11_strategie-deploiement-par-communaute.md), [raw/transcripts/2026-09-11_strategie-entites-et-makers.md](../../../raw/transcripts/2026-09-11_strategie-entites-et-makers.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-11 freelance-channel-communication-plan](../strategy/2026-09-11_freelance-channel-communication-plan.md)
- [2026-09-11 freelance-deck-v1 expert-review](2026-09-11_freelance-deck-v1_expert-review.md)
- [2026-09-11 launch-plan-90-days](../strategy/2026-09-11_launch-plan-90-days.md)
- [2026-09-11 problem-structure-dedup-spec](2026-09-11_problem-structure-dedup-spec.md)
- [2026-09-11 team-skills-audit](../strategy/2026-09-11_team-skills-audit.md)
- [2026-09-12 target-communities-map](../strategy/2026-09-12_target-communities-map.md)
- [2026-09-12 trainers-cards-candidates](2026-09-12_trainers-cards-candidates.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
