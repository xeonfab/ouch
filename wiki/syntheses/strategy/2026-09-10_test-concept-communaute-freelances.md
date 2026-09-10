---
last_reviewed: 2026-09-10
---

# Test de concept Ouch! — communauté freelances fermée

> One-line TL;DR: message + structure de landing page pour exécuter le test de validation publique jamais lancé, ciblé sur un groupe fermé de freelances (Slack/FB/Discord) où Fabien a un accès réel.

| Field | Value |
|---|---|
| **Date** | 2026-09-10 |
| **Type** | strategy (growth experiment, non exécuté) |
| **Participants** | Fabien (founder/PM), agent `ouch-growth-hacker` |
| **Source(s)** | Conversation de conception, ancrée sur l'item ouvert "Run the long-planned public validation test" ([synthèse projet complète](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md)) |

---

## Contexte

Le test de validation publique du concept (partager des liens et observer les réactions spontanées) était identifié comme action ouverte, jamais exécutée, dans la synthèse de contexte complet du projet. Cette page opérationnalise cette action : un canal précis (groupe fermé de freelances), un message adapté à ce canal, et une structure de landing page.

Décision de ciblage : un seul canal où Fabien a un accès réel plutôt qu'une diffusion large (LinkedIn public, email froid) — cohérent avec la règle du growth hacker Ouch! de cibler une population à la fois plutôt qu'un lancement mainstream dilué.

## Décisions clés

- **Canal retenu** : groupe fermé de freelances (Slack/Facebook/Discord), pas LinkedIn public ni email froid — accès réel de Fabien, meilleur taux de réponse.
- **Storage** : test exécuté sur le prototype `localStorage` actuel, sans attendre la migration Supabase — objectif = engagement qualitatif (accroche, justesse des frustrations) et taux de capture email, pas preuve sociale en temps réel partagée.
- **Double CTA sur la page** : réagir aux problèmes existants (swipe) **et** proposer son propre problème (réutilise le flow `qualifyProblem` déjà buildé) — les deux actions à parité visuelle, pas l'une en soft-CTA sous l'autre.
- **Ton du message** : adapté aux normes d'un groupe fermé (anti pur growth hacking déguisé) — présenté comme une demande d'avis franc de pair à pair, pas une promotion produit.

## Message à poster dans le groupe

> Salut à tous 👋
>
> Je sollicite pas souvent le groupe, mais j'ai besoin de vrais avis de freelances sur un truc que je bricole sur mon temps libre.
>
> Le constat de départ : on a tous des frustrations récurrentes (clients qui traînent à payer, admin qui bouffe des heures, outils mal foutus...) qu'on balance sur Twitter ou entre nous, sans que ça aille jamais nulle part. Je construis **Ouch!** pour en faire un catalogue de problèmes vraiment validés, que des devs/no-coders puissent venir résoudre.
>
> Ça marche comme ça : vous **swipez** des frustrations de freelances (droite = "ça m'arrive", gauche = "pas concerné"), et si un truc vous parle vraiment, vous laissez votre email pour être prévenu si une solution sort un jour. **Et si la vôtre n'y est pas, vous l'ajoutez.**
>
> Ce que je cherche à savoir : est-ce que ces problèmes sonnent vrai, est-ce qu'il en manque des évidents, et est-ce que le format donne envie d'aller au bout.
>
> 👉 [lien]
>
> 2 minutes chrono. Un retour franc en commentaire (même "aucun intérêt") m'est hyper utile. Merci 🙏

## Structure de la landing page de test

Une entrée dédiée (pas `/terminal`, pas la home générale), réutilisant les composants existants :

1. **Header** : "Salut [nom du groupe] 👋" + accroche en une phrase
2. **Deck de 6-10 cartes freelance curatées** (les meilleures du catalogue existant sur facturation/clients qui paient en retard/admin/charge mentale) → swipe
3. **Capture email au swipe droit** (comportement déjà existant, rien à recoder)
4. **CTA "Ton problème n'y est pas ? Ajoute-le"**, à parité visuelle avec le deck de swipe (pas en lien discret bas de page) → réutilise le flow `qualifyProblem` déjà buildé (texte libre → reformulation IA → aperçu → publication)
5. **Fin de deck : micro-questionnaire 2 questions** — "Ces frustrations sonnent vrai pour toi ?" (oui/non) + "Un truc qui te frustre et qu'on n'a pas listé ?" (texte libre) — double usage : feedback qualitatif + sourcing de contenu

## Mesures à suivre

Échantillon petit → lecture qualitative prioritaire sur le %, en particulier les réponses ouvertes du questionnaire.

- Taux de swipe droit sur les cartes proposées
- Taux de capture email sur swipe positif
- Nombre de problèmes ajoutés spontanément via le flow `qualifyProblem`
- Réponses ouvertes du micro-questionnaire (signal qualitatif sur le wording)

## Decisions & next steps

| Owner | Action | Due | Status |
|---|---|---|---|
| Fabien | Choisir/valider le groupe fermé précis à cibler | — | open |
| Fabien | Brief Lovable pour la page filtrée (6-10 cartes freelance + CTA soumission à parité + micro-questionnaire fin de deck) | — | open |
| Fabien | Sélectionner les 6-10 meilleures cartes freelance du catalogue existant | — | open |
| Fabien | Poster le message dans le groupe et suivre les métriques ci-dessus | — | open |

## Related wiki pages

- Syntheses: [Ouch!/FixMyLife — full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md) (item ouvert dont ce test découle)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
