---
last_reviewed: 2026-09-11
---

# Dépôt d'un problème — décision du panel double-face

> One-line TL;DR: Fabien a demandé à "toute l'équipe" de repenser le flow de dépôt d'un problème pour qu'il soit aussi simple qu'un tweet mais totalement accompagné ; le panel-ouch-double-face a découvert que la majorité du brief était déjà construite, et a resserré le scope au seul vrai manque : le partage social.

| Field | Value |
|---|---|
| **Date** | 2026-09-11 |
| **Type** | strategy (décision de panel délibératif) |
| **Participants** | Fabien (founder/PM), skill `panel-ouch-double-face` (Karim/CEO, Yasmine/Growth, Marc/CTO, Léa/persona victime, Julien/persona maker) |
| **Source(s)** | Brief brut de Fabien adressé à "toute l'équipe" (verbatim ci-dessous), lecture du code existant (`submit-flow.tsx`, `qualify.functions.ts`, `duplicate.functions.ts`) |

---

## Contexte

Fabien a soumis un brief à toute l'équipe produit sur le flow de dépôt d'un problème (côté victime), avec l'objectif explicite : "le plus simple possible, le plus clair, qu'on ne concurrence vraiment [pas] l'ajout d'un tweet — comme Twitter, encore plus simple — et que l'on accompagne parfaitement, soucieux du problème de nos utilisateurs. Et comme quoi ça va être écouté et pris en considération."

Brief brut (besoins listés, pas encore une spec) :
- L'utilisateur peut écrire beaucoup ; l'IA en fait un message concis (1-2 phrases) pour le swipe, le reste en description détaillée
- Suggérer les problèmes très similaires et inciter à la mutualisation (concentrer l'impact/score plutôt que le fragmenter)
- Pouvoir déposer avec ses propres mots malgré tout
- Suggestions de reformulation
- Suggestions de liaison d'entité(s)
- Questions de clarification pour rendre le problème plus clair/impactant
- Pouvoir partager le problème déposé une fois publié

## Découverte clé avant le panel

En lisant le code existant (`src/components/ouch/submit-flow.tsx`, `src/lib/qualify.functions.ts`, `src/lib/duplicate.functions.ts`) avant de lancer la délibération, il est apparu que **la majorité du brief était déjà construite**, d'une session précédente :

| Besoin du brief | État réel |
|---|---|
| Concision (carte) + détail (description) | ✅ déjà là — `statement` forcé à 90-180 caractères par le prompt IA, `synthesis` conserve le récit complet |
| Mutualisation / suggestion de doublon | ✅ déjà là, et plus avancé que prévu — `detectDuplicate` compare par IA (pas juste un filtre secteur/thème) le nouveau problème aux existants du même secteur/sous-thème, score de confiance ≥ 0.7, propose "C'est le même, je vote pour celui-là 🔥" |
| Déposer avec ses propres mots | ✅ déjà là — bouton "Modifier le texte" sur la formulation proposée |
| Reformulation | ✅ déjà là — 2-3 variantes proposées par `qualifyProblem` |
| Liaison d'entité | ✅ déjà là — suggérée, jamais auto-liée, confirmation explicite via toggle |
| Questions de clarification | ❌ absent |
| Partage social après publication | ❌ absent — le succès affichait un simple toast |

## Décision du panel (synthèse)

**Ancrage** : le dépôt de problème est le seul canal de contenu qui vient des utilisateurs eux-mêmes, et il arrive au moment précis où le tout premier test réel (communauté freelance) démarre sans encore aucune soumission observée. Risque : sur-équiper le flow avant d'avoir vu un vrai dépôt casserait la promesse "plus simple qu'un tweet".

**Décision retenue** : ne construire que le partage social (priorité growth — Yasmine : chaque dépôt partagé est un point d'entrée gratuit vers la plateforme). La clarification à une relance est mise de côté — la mutualisation déjà en place couvre déjà une bonne partie du sentiment d'accompagnement, et Léa (persona victime) reste vigilante sur toute friction ajoutée avant publication.

**Ce qui n'est pas fait maintenant** :
- Détection sémantique de doublons plus poussée (déjà satisfaisante en l'état)
- Questions de clarification IA — reporté, à réévaluer une fois des soumissions réelles observées sur le test freelance
- Génération d'image de partage personnalisée — texte + lien suffisent pour le MVP

## Build status

**Partage social** (`submit-flow.tsx`, fonction `publish()`) — livré :
- Après publication réussie, le toast de succès propose un bouton "Partager ma carte 📣" (action du toast `sonner`, non bloquant)
- Mobile : `navigator.share()` avec titre/texte/lien du site
- Desktop : ouverture d'un intent de partage X pré-rempli (texte + lien), dans un nouvel onglet
- Texte de partage généré à partir du `statement` publié : `"${text}" — je viens de le signaler sur Ouch! 💥`

**Refonte "meilleure expérience de création" (audit `critique-ux`, score initial 2,9/5) — livrée le 2026-09-11, commit Lovable `51b724a`** :

Fabien a ensuite demandé "la meilleure expérience de création d'un problème". L'audit UX a relevé trois frictions : la connexion Google exigée avant même d'écrire (valeur demandée avant d'être montrée), un choix imposé entre 3 variantes IA (Hick), et un simple toast à la publication (aucun moment "je suis écouté"). Puis, en test réel, Fabien a pointé l'écran de preview qui empilait trois questions à la fois (note de reformulation + carte de doublon + choix de formulation). Décision : **une question par écran**. Livré dans `submit-flow.tsx` (+ `submit-modal.tsx`) :
- **Connexion au moment de publier, pas avant** : un visiteur écrit, lance l'analyse, voit et modifie sa carte sans compte. Le bloc "Connecte-toi pour publier" n'apparaît qu'à la place du bouton Publier. Le brouillon (récit, draft IA, formulation, entité) survit à la redirection OAuth via `sessionStorage` (`ouch.submitDraft`) et la modale se rouvre automatiquement sur la preview au retour de Google.
- **Une carte directement** : la première variante IA est sélectionnée d'office et affichée comme carte ; "Autre formulation 🔁" fait défiler les variantes sans écran de liste. La note de reformulation (`flagReason`) est déplacée dans la carte, sous la formulation, en discret.
- **Étape "doublon" dédiée, avant la carte** : `detectDuplicate` est désormais enchaîné pendant le chargement (5e étape "On vérifie si quelqu'un l'a déjà signalé…"). Si correspondance, écran à question unique "Quelqu'un a déjà signalé ça 👀" : carte existante rendue comme dans le produit, ligne de preuve sociale (🔥 concerné·es · douleur /100), rappel du récit de l'utilisateur, primaire "C'est le même — je rejoins cette carte 🔥", secondaire "Non, le mien est différent → continuer". Plus aucun bloc doublon empilé sur la preview.
- **Écran de succès** (`step = "published"`, deux modes) : "Ta carte est en ligne 🎉" (création) ou "Ta voix est comptée 🔥" (rejoint un doublon), carte publiée telle qu'elle apparaîtra dans le swipe, promesse "On te prévient dès qu'un maker s'empare de cette carte", actions Partager 📣 / Voir dans le Swipe / Déposer un autre problème. La modale ne se ferme plus avant que l'utilisateur ait vu sa carte. "Valider" renommé "Créer ma carte ✨".

Résolu (commit Lovable `81a51e5`) : rejoindre un doublon sans être connecté affichait une promesse de notification sans capturer d'email. Désormais, sur l'écran "Ta voix est comptée 🔥", si l'utilisateur n'est pas connecté, la ligne de promesse est remplacée par un bloc "Connecte-toi pour être prévenu·e dès qu'un maker s'en empare" + bouton Google. L'id de la carte est persisté en `sessionStorage` (`ouch.pendingLeadProblemId`, même clé que le swipe) avant la redirection, et le lead est enregistré au retour (idempotent, un seul email par carte) avec un toast "C'est noté, on te prévient ✉️".

## Exemples de test fournis à Fabien

Deux récits bruts à coller dans "Déposer ma frustration" pour valider le flow complet :
1. Un récit proche du problème Qonto déjà catalogué (id 36) → doit déclencher `detectDuplicate` et proposer de voter pour l'existant
2. Un récit inédit (relance d'acompte après devis signé) → doit produire 3 variantes fraîches, sans doublon détecté, sans entité liée

## Related wiki pages

- Syntheses: [Test de concept — communauté freelances](2026-09-10_test-concept-communaute-freelances.md) (le CTA "Déposer ma frustration" testé ici réutilise ce flow)
- Syntheses: [Ouch!/FixMyLife — full project context](../projects/2026-09-10_ouch-fixmylife-contexte-complet.md)
- MOC: [Ouch! / FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

---

<!-- BACKLINKS:START -->
## Referenced by

**Syntheses**

- [2026-09-10 test-concept-communaute-freelances](2026-09-10_test-concept-communaute-freelances.md)

**Other**

- [📇 Wiki Index](../../index.md)

**Mocs**

- [MOC Ouch FixMyLife](../../mocs/MOC_Ouch_FixMyLife.md)

<!-- BACKLINKS:END -->
