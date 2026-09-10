# Ouch! / FixMyLife — Contexte complet du projet

> Document de reprise de contexte, généré à partir de l'historique complet des décisions produit.
> Projet Lovable : **fix-it-karma**, affiché publiquement "FixMyLife" / "Ouch!"
> Éditeur : https://lovable.dev/projects/08a02fd1-5717-42d4-9ff0-22edffc21ca2

---

## 1. Concept et pitch

Ouch! (alias "Tinder des problèmes") est une plateforme communautaire à deux faces :

- **Côté "victimes"** : les utilisateurs swipent des cartes de frustrations du quotidien, formulées à la première personne. Swipe à droite = "j'ai ce problème et ça me rend fou" (vote positif). Swipe à gauche = indifférence. Après un swipe positif, proposition de laisser un email pour être prévenu quand une solution existe.
- **Côté "makers"** : un dashboard ("Terminal Maker") classe les problèmes par **Score de Douleur** (45% volume de votes positifs, 35% taux de conversion, 20% emails opt-in collectés), permettant à un entrepreneur de trouver un marché déjà validé avant de coder quoi que ce soit.

Le projet est piloté par Fabien avec un temps disponible limité (~20h/semaine, en parallèle d'un poste permanent chez Agicap et d'une activité de conseil via sa SASU).

---

## 2. Modèle économique

- **Swipe gratuit et illimité** côté victimes — le volume de données EST le produit, aucune monétisation de ce côté.
- **Monétisation côté makers uniquement** :
  - Abonnement Pro (accès aux données démographiques détaillées) — fourchette envisagée 15-40€/mois, calibrée pour un solopreneur en auto-financement.
  - Vente de listes d'emails opt-in par problème — nécessite une mise à jour du texte de consentement si activée (le consentement actuel ne couvre que "être prévenu d'une solution", pas la revente à un tiers).
- **Règle produit dure** : une entité réelle citée sur une fiche PEUT devenir cliente payante du Terminal Maker (accès aux données comme n'importe quel maker), mais **sans statut différencié ni démarchage commercial actif de notre part** — canal strictement passif et opportuniste. Aucun rôle "entité officielle" ne doit exister dans le modèle de comptes.
- **Timing de monétisation** : ne pas activer de paywall avant le signal de traction défini (voir section 4). Le mot "pétition"/vocabulaire pétition avait été envisagé puis nuancé (voir section 8).
- **Fonctionnalité mise en réserve (v2 Pro)** : suggestions IA de besoins/idées business inférées par regroupement de plusieurs problèmes similaires — jugée trop risquée à montrer avant d'avoir un vrai volume de données (Julien/persona Maker : "si les idées suggérées sont évidentes ou génériques, je perds confiance instantanément"). À teaser sur `/devenir-maker` sans la construire pour l'instant.

---

## 3. Équipe d'agents (skills Claude) créée

Situées dans `/mnt/skills/user/`, à invoquer par nom ou par déclenchement naturel :

| Skill | Rôle |
|---|---|
| `ouch-ceo` (Karim) | Vision, priorisation, roadmap, arbitrages — filtre systématique : "est-ce que ça résout le cold start maintenant ?" |
| `ouch-growth-hacker` (Yasmine) | Amorçage double-face (victimes + makers), pipeline scraping/automatisation (Make/n8n), copywriting |
| `ouch-cto` (Marc) | Faisabilité technique Lovable/Supabase, dette technique, arbitrages build vs report |
| `ouch-ux-designer` | Cohérence visuelle, double registre (fun côté victimes / factuel côté makers) |
| `ouch-cfo` | Pricing, unit economics, timing de monétisation |
| `ouch-legal` | Risque de nommer des entités réelles, RGPD, diffamation/dénigrement, grille de modération |
| `ouch-persona-victime` (Léa, freelance graphiste à Lyon) | Test du wording et de l'UX côté swipe |
| `ouch-persona-maker` (Julien, développeur indépendant sceptique) | Test de la valeur perçue côté Terminal/pricing |
| `panel-ouch-double-face` | Panel délibératif à 4 tours pour les décisions structurantes, avec ancrage systématique sur le risque de démarrage à froid (cold start) |

---

## 4. Stratégie de lancement

**Principe validé** : cibler une seule population à la fois plutôt qu'un lancement mainstream, pour ne pas diluer un temps de travail limité entre plusieurs tons de contenu.

- **Cercle 1 (actuel)** : freelances/créateurs. Raisons : frictions faciles à formuler en une phrase, forte présence sur les canaux scrapables (Reddit, Indie Hackers, Twitter/X), cycle de décision d'achat rapide (paient seuls, sans comité).
- **Signal de bascule vers le cercle 2 (PME)** : 3 problèmes freelances avec score de douleur >70 **et** au moins 1 maker qui revient une deuxième fois sur le Terminal. Pas de date fixe, un signal de traction.
- **Cercle 3 envisagé** : grand public / citoyens (frictions administratives et institutionnelles) — déjà partiellement présent via les secteurs Lifestyle/Santé/Mobilité et les entités institutionnelles (France Travail, URSSAF, CAF).
- **Distinction importante actée** : la restriction "freelance d'abord" s'applique uniquement à **qui on démarche activement comme futur client payant** — jamais au contenu du feed ni à sa diffusion virale, qui peuvent et doivent rester larges dès maintenant (le contenu institutionnel/administratif touche autant les freelances que le grand public).

---

## 5. Positionnement — ce qu'Ouch! N'EST PAS

Comparatif établi face à plusieurs références :

- **Twitter/X** : exutoire immédiat sans agrégation dans la durée, aucune capture d'intention d'achat. Ouch! ne concurrence pas la portée immédiate de Twitter — au contraire, Twitter est une source à scraper pour peupler le feed, pas un concurrent.
- **Trustpilot** : vend un score de confiance à la marque elle-même pour aider un choix d'achat. **Rejeté comme modèle** — Ouch! n'a pas vocation à juger une marque, aucune fonctionnalité de réponse publique de l'entité, aucune notation/étoiles, aucun classement "pire entreprise".
- **Mention / Mentionlytics / Brandwatch** (social listening) : payés par la marque pour se surveiller elle-même (41-249€/mois). Ouch! inverse le client payeur (un tiers exploite la friction, pas la marque qui la corrige) et ajoute une capture d'intention (emails opt-in) que le social listening ne fait jamais.
- **Change.org** : le modèle le plus proche en apparence (compteur, vocabulaire "signature" envisagé), mais structurellement différent — une pétition Change.org **argumente et propose elle-même la solution**, demande au décisionnaire nommé de l'exécuter. Ouch! sépare : la victime signale juste (une phrase courte), un maker tiers (pas forcément l'entité) invente la solution ensuite. Change.org vend la pression sur un décideur ; Ouch! vend une opportunité de marché à une équipe qui va résoudre et en tirer un revenu.
- **Positionnement propre résumé (persona Julien)** : *"je n'ai jamais vu d'outil de social listening qui me sort '340 personnes veulent une solution à CE problème précis, voici leurs emails'."*

---

## 6. Règles produit dures (non négociables)

1. **Entité = organisation uniquement, jamais une personne physique.** Un maire, un élu, un responsable identifiable ne peut jamais être tagué comme entité — régime juridique différent (vie privée) d'une organisation (dénigrement commercial). Si le récit nomme une personne, aucune entité n'est taguée, même si une organisation est associée au contexte. Règle intégrée dans le prompt système de `qualifyProblem`.
2. **Pas de sujets de politique publique clivants.** Décision prise en écartant explicitement un positionnement "société"/présidentielle (élection au 18 avril / 2 mai 2027). L'angle **civisme** est validé (documenter des frictions de service public), mais jamais de prise de position sur une politique (ex: quotas migratoires, projets de loi) — uniquement des frictions *administratives* factuelles (délais, bugs, opacité) contre une institution.
3. **Terminologie : toujours "entité", jamais "organisation"** dans l'interface visible.
4. **Aucun statut spécial pour une entité cliente.** Une entité qui s'abonne au Terminal est un maker comme un autre.
5. **Pas de démarchage commercial actif vers les entités citées** (rejeté explicitement : tweeter une liste de problèmes à une entreprise nommée pour l'inciter à créer un compte — contredit le canal passif et réintroduit un risque de "name and shame").
6. **Pas de suppression de contenu**, jamais, sur demande de l'entité ni du maker (sauf obligation légale) — le texte du problème et son historique de score restent visibles indéfiniment. Seuls les emails suivent une politique de conservation RGPD distincte, avec droit à l'effacement individuel.
7. **Pas de fil de discussion / droit de réponse.** Les mises à jour maker et les "voix des concernés" sont à sens unique, jamais un chat.
8. **Ton toujours fun/ludique**, y compris pour les sujets institutionnels ou civiques — jamais pédagogique ou administratif dans l'écriture des cartes.

---

## 7. Registre de modération / grille juridique (agent `ouch-legal`)

Principe central : chaque carte doit rester un **fait vécu individuel, factuel et descriptif** — jamais un jugement de valeur sur l'entité elle-même.

- Interdits : "malhonnête", "arnaque", "nul", "inacceptable", "vol", "escroquerie" et équivalents — y compris dans les verbatims.
- OK : "j'attends mon remboursement depuis 3 semaines" ; À corriger : "cette entreprise est malhonnête".
- Une relecture manuelle a déjà été appliquée sur 33 cartes du catalogue (4 corrections : Qonto, Malt, Stripe, Impots.gouv).
- Cette règle est désormais **intégrée nativement dans le prompt système de `qualifyProblem`** (IA de dépôt), avec détection préalable (`flagged`/`flagReason`) plutôt que correction a posteriori.
- **Distinction Type A / Type B** (champ `resolutionType`) :
  - **Type A "tiers"** : contournable par un maker externe sans l'entité (ex. SNCF Connect remboursement, Doctolib RDV annulé).
  - **Type B "entite"** : résolution impossible sans l'entité elle-même (ex. Qonto compte bloqué, France Travail bug de connexion).
  - Le disclaimer de communication publique doit différer selon le type — jamais une seule affirmation valable pour tout le catalogue.
  - Badges reformulés en langage clair : "🛠️ Une solution externe est possible" / "🔒 Seule l'entité concernée peut résoudre ça".

---

## 8. Vocabulaire "pétition" — décision nuancée

- Le vocabulaire pétition (verbe "signer", "signatures") avait été validé en principe pour sa puissance de conversion, à condition d'un disclaimer honnête sur le mécanisme réel de résolution (maker tiers, pas forcément l'entité).
- Cette décision a ensuite été affinée par la distinction Type A/B (le disclaimer ne peut pas être unique).
- **Statut réel dans l'app aujourd'hui** : le vocabulaire "signer/signatures" n'a jamais été envoyé à Lovable — l'app utilise toujours "concerné(e)s" et l'icône 🔥. Vocabulaire à trancher définitivement avant tout lancement public si on veut l'adopter.

---

## 9. Modèle de données (état construit)

- **Problem** : id, statement (1ère personne), title (3ème personne, doit contenir un élément concret/spécifique — fréquence, chiffre, contexte précis, jamais générique), sector, topic (sous-thématique), status, `resolutionType` ("tiers"/"entite"), `topicHashtag` (toujours généré, contexte/lieu/thème, ne nomme jamais une entité), entité(s) liée(s) (optionnel), seeds de votes.
- **Vote** : problemId, direction (right/left), timestamp.
- **Lead** : problemId, email, timestamp (consentement = "être prévenu d'une solution" uniquement).
- **Entity** : nom, type (Entreprise / Institution publique), secteur, description, slug (route `/entite/:slug`).
- **Statuts de cycle de vie d'un problème** : `Incubation` → `Maker assigné` → `🔍 À confirmer` (nouveau) → `✅ Résolu` (si majorité de confirmation des votants d'origine, seuil minimum 5 réponses) ou retour à `Maker assigné` (si rejeté).
- **Secteurs** : B2B, Lifestyle, Fintech, Santé, Mobilité — avec sous-thématiques par secteur (ex. B2B → RH/Ventes/Finance/Ops).
- **13-16 entités réelles nommées et sourcées** à ce jour : SNCF Connect, Doctolib, France Travail, URSSAF Auto-Entrepreneur, Colissimo, Impots.gouv, CAF, Qonto, Malt, Stripe + 3 génériques (opérateur télécom, banque pro, marketplace e-commerce — volontairement non nommés faute de source assez solide).
- Stockage actuel : **`localStorage` côté client** (pas de partage réel entre utilisateurs) — bascule vers **Supabase identifiée comme le vrai chantier technique en attente**, nécessaire avant un vrai lancement public pour que les votes/scores soient crédibles et partagés.

---

## 10. Fonctionnalités construites / en cours (état à la dernière session)

✅ **Terminé et validé chez Lovable** :
- Swipe deck avec animation Framer Motion, filtrage par secteur/sous-thème.
- Terminal Maker avec Score de Douleur, filtres, panneau détail.
- Fiches entité `/entite/:slug` avec double niveau (vue publique légère / vue Maker détaillée).
- Dépôt de problème assisté par IA (`qualifyProblem`) : saisie libre → reformulation → preview → publication. Propose désormais **2-3 variantes** au lieu d'une seule reformulation imposée, avec détection préalable de contenu problématique (`flagged`/`flagReason`).
- Chip de confirmation explicite du lien entité (jamais de lien automatique silencieux).
- Écran de dépôt transformé en **grand modal** (au lieu d'un encart dans la page), avec confirmation avant fermeture si texte non vide.
- Home hub restructurée : bandeau d'action (Swiper / Déposer), Tendances globales, par thématique (renvoie vers `/swipe` filtré, PAS vers `/terminal`), par entité, Hall of Fame redescendu.
- Relecture juridique complète du catalogue (grille fait vs jugement de valeur).
- Hashtag de sujet (`topicHashtag`) toujours généré, distinct de l'entité.
- Fonctionnalité "🗣️ Voix des concernés" : mini-témoignage optionnel (60 caractères) après un swipe positif, modéré par filtrage de mots-clés.
- Illustration IA pour les cartes en tendance (déclenchement manuel/seuil, jamais systématique, style flat cohérent avec la charte, interdiction stricte de représenter une marque/logo réel).
- Badges de résolution retirés des cartes compactes (home), conservés uniquement dans les vues détaillées (Swipe, Terminal, fiche entité).

🔄 **Envoyé à Lovable, statut à vérifier à la reprise** :
- Statut "🔍 À confirmer" + mécanisme de vote de confirmation par les votants d'origine (condition pour afficher honnêtement "✅ Résolu grâce à vous").
- Mélange du deck de swipe avec des cartes de célébration ("✅ Résolu grâce à vous") et mises en avant de "Voix des concernés" marquantes (ratio ~1 pour 8-10 cartes de problème), pour casser la monotonie négative du flux.
- Pages légales : `/mentions-legales`, `/confidentialite`, `/cgu` (à vérifier si complètement terminées).
- Qualification Type A/B rétroactive de tout le catalogue existant.

⏳ **Décidé mais jamais envoyé à Lovable** (à vérifier/relancer) :
- File d'attente d'entités suggérées par l'IA (au-delà des 13-16 fermées), à valider manuellement plutôt que publiées automatiquement — pont vers une future création plus ouverte.

🚫 **Explicitement écarté** :
- Création libre d'entités par tout utilisateur façon Twitter/@handle (reporté à après la bascule Supabase + signal de traction).
- Positionnement société/présidentielle explicite.
- Démarchage actif des entités par tweet public.
- Toute mention de personne physique comme entité.
- Fonctionnalité de suggestion IA de besoins/idées business (reportée en v2 Pro, nécessite du volume réel).

---

## 11. Sitemap validé

**Registre victimes (ludique, néo-brutaliste)** : `/`, `/swipe`, `/entite/:slug`, dépôt via modal.
**Registre makers (factuel/sombre)** : `/terminal`, `/devenir-maker` (léger, pricing "bientôt" + capture email).
**Légal** : `/mentions-legales`, `/confidentialite`, `/cgu`.
**Reporté** : page "À propos"/blog SEO, page de contact dédiée aux entités, tout système de facturation réel.

---

## 12. Identité visuelle et ton

- Style néo-brutaliste/playful : jaune, violet, vert menthe, bordures marquées, ombres portées (`pop`/`pop-sm`), confettis.
- Double registre à ne jamais mélanger : ludique/fun pour tout ce qui touche aux victimes (y compris sur des sujets institutionnels), factuel/sombre uniquement pour le Terminal Maker.
- Règle de concision : les cartes doivent être lisibles en 2 secondes (persona Léa). Titres et statements doivent contenir un élément concret et spécifique (chiffre, fréquence, contexte), jamais une formulation générique.
- Illustrations IA (si générées) : flat, cohérentes avec la charte, jamais de photoréalisme, jamais de logo/livrée de marque reconnaissable.

---

## 13. Prochaines étapes en attente

1. Vérifier l'état d'avancement complet des derniers envois Lovable (statut "à confirmer", pages légales, mélange du deck).
2. Lancer enfin le **test public de validation** planifié depuis plusieurs sessions : partager les liens `/entite/:slug` sur les réseaux et observer si des makers réagissent spontanément — ce test n'a toujours pas été exécuté à ce stade.
3. Trancher définitivement le vocabulaire "signer/signatures" vs "concerné(e)s" avant tout partage public large.
4. Décider si/quand construire la bascule Supabase (persistance réelle, authentification SSO pour le dépôt, ouverture progressive de la création d'entités).
