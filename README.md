# Damier — Entraîneur de Dames Internationales (V1)

Application 100 % gratuite, jouable hors ligne, sans compte ni carte bancaire.

## Ce que contient cette V1

- Plateau 10×10 tactile (portrait/paysage automatique), zoom fluide sur mobile.
- Moteur de règles FMJD complet : prise obligatoire, **prise maximale**, dames volantes (longue portée), promotion — **y compris la promotion en cours de rafle multiple** (corrigé en V2, voir plus bas).
- Mode Joueur contre Joueur et mode contre IA (5 niveaux : débutant → expert), moteur minimax + élagage alpha-bêta.
- Panneau « Coach virtuel » : questions socratiques avant de jouer (centre, menaces, coups candidats, plan) + bouton d'analyse de position.
- Historique des coups, compteur de prises/coups, annulation.
- Fonctionne 100 % hors ligne une fois ouverte une première fois (aucun appel réseau dans le jeu).

## Nouveautés V2 (déjà livrées)

- **Promotion en cours de rafle corrigée** : un pion qui atteint la dernière rangée pendant une prise multiple devient dame immédiatement et peut continuer la rafle avec les pouvoirs de la dame (règle FMJD stricte), même s'il termine son parcours ailleurs que sur la dernière rangée.
- **Rapport après partie** : à la fin de chaque partie, un panneau « Rapport de partie » liste les 3 coups les plus coûteux (détectés en comparant, à chaque coup humain, l'évaluation du coup joué à celle du meilleur coup possible) et affiche un **niveau estimé indicatif** (heuristique basée sur la perte moyenne par coup, pas un vrai classement Elo).
- **Entraînement quotidien** : un panneau propose chaque jour une question de réflexion, une piste tirée de ta dernière erreur marquante, et **5 exercices tactiques** (rafles doubles/triples, dames volantes) piochés dans une bibliothèque de combinaisons vérifiées et tournant chaque jour. Chaque exercice est validé automatiquement (bonne case d'arrivée = coup correct) avec une explication du motif.
- Les parties et la progression aux exercices sont conservées dans le stockage local du navigateur (`localStorage`) — aucune donnée n'est envoyée en ligne.

## Nouveautés V3 (déjà livrées)

- **Coach réactif** : après chaque coup joué (par toi ou par l'IA), le coach commente le coup réellement joué — combinaison réussie, prise ouverte pour l'adversaire, perte ou gain de contrôle du centre — au lieu de poser une question générique à chaque fois. Une question de réflexion reste affichée en complément avant ton prochain coup.
- **Programme d'apprentissage complet** : 20 fiches réparties sur les 4 niveaux prévus (débutant stratégique, joueur de club, joueur avancé, expert), avec les contenus exacts demandés — centre, mobilité, structures, chaînes de pions, tenaille, encerclement, marchand de bois, systèmes Roozenburg et Keller, sacrifices positionnels, finales, calcul profond, etc. Les définitions techniques (tenaille, marchand de bois, Roozenburg) sont vérifiées auprès de sources spécialisées (FFJD) plutôt qu'inventées. Progression de lecture suivie localement (case cochée par fiche lue).

## Nouveautés V4 (déjà livrées)

- **Bibliothèque de parties historiques** : une première partie réelle et sourcée (C. Dorland – Piet Roozenburg, 1951, retranscrite d'après un document pédagogique FMJD) est intégrée avec un lecteur pas-à-pas (◀ Précédent / Suivant ▶). Chaque coup a été **revalidé automatiquement par le moteur de règles** de l'application avant intégration : les 91 demi-coups de la partie sont tous légaux au regard des règles FMJD implémentées, ce qui garantit qu'aucune transcription erronée n'a été insérée. L'évaluation du moteur (matériel + position) s'affiche à chaque coup, pour comparer l'appréciation de l'application à la partie réelle.
- **Tableau de bord de progression persistant** : chaque partie terminée alimente un historique local (niveau estimé, nombre d'erreurs, résultat) affiché sous forme de mini-graphique en barres, avec le nombre de parties analysées, le niveau moyen et le taux de victoire contre l'IA.
- Le stockage repose sur `localStorage` (déjà utilisé en V2/V3) plutôt que sur IndexedDB : pour le volume de données de cette application (quelques dizaines de parties, six exercices), c'est fonctionnellement équivalent et plus simple à maintenir. Une migration vers IndexedDB resterait pertinente uniquement si la bibliothèque de parties et l'historique grossissaient significativement.

## Limitation connue de cette version

L'analyse post-partie et le coach réactif restent des **heuristiques légères** (recherche à profondeur 3, comparaison d'évaluation avant/après) : elles donnent une bonne indication des schémas les plus flagrants (rafle manquée pour l'adversaire, perte de centre) mais ne remplacent pas une analyse moteur complète. Le « niveau estimé » est indicatif et non un Elo officiel. Le contenu du niveau 3 sur le système Keller reste volontairement général, faute de sources suffisamment détaillées sur son contenu précis. La bibliothèque de parties ne compte pour l'instant qu'une seule partie complète — volontairement, pour garantir que chaque partie ajoutée est intégralement vérifiée coup par coup plutôt que copiée sans contrôle.

## Installer comme application (PWA) — gratuit, sans magasin d'applications

1. Créez un dépôt GitHub public et déposez les 3 fichiers (`index.html`, `manifest.json`, `sw.js`).
2. Activez **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / racine). C'est gratuit, sans carte bancaire.
3. Ouvrez l'URL fournie par GitHub Pages sur le téléphone :
   - **Android (Chrome)** : menu ⋮ → « Ajouter à l'écran d'accueil ».
   - **iPhone (Safari)** : bouton Partager → « Sur l'écran d'accueil ».
4. L'icône apparaît comme une application native ; elle fonctionne ensuite hors ligne.

Alternative sans GitHub : Netlify Drop (netlify.com/drop) — glisser le dossier, gratuit, aucune carte bancaire.

## Feuille de route (comme demandé dans le brief)

**V2 — Analyse & entraînement (livré ✅)**
- ~~Rapport après partie (erreurs critiques, coups manqués, Elo estimé).~~
- ~~Générateur d'exercices tactiques quotidiens (5 tactiques/jour).~~
- ~~Corriger la promotion en cours de rafle (règle FMJD stricte).~~
- Reste à faire si besoin : ajouter une vraie « position stratégique du jour » notée par le moteur (pour l'instant, seule la question de réflexion tourne quotidiennement), et enrichir la bibliothèque de tactiques (6 combinaisons vérifiées actuellement).

**V3 — Coach intelligent & pédagogie (livré ✅)**
- ~~Parcours de cours structuré (centre, chaînes de pions, Roozenburg, Keller, tenaille, sacrifices).~~
- ~~Le coach commente réellement le coup joué (pas seulement des questions génériques) via une petite bibliothèque de motifs tactiques détectés automatiquement.~~
- Reste à faire si besoin : illustrer certaines fiches (tenaille, marchand de bois) par une position jouable sur le damier, comme les exercices tactiques.

**V4 — Bibliothèque & progression (livré ✅)**
- ~~Base de parties historiques annotées.~~ (une partie sourcée et vérifiée pour l'instant — facile à enrichir : voir ci-dessous)
- ~~Tableau de bord Elo/progression persistant.~~
- Reste à faire si besoin : ajouter d'autres parties historiques (chaque ajout doit être revalidé coup par coup par `legalMoves`/`applyMove` avant intégration, comme pour la première), et des finales théoriques annotées (dame contre pions, oppositions) en réutilisant le même mécanisme que les exercices tactiques.

## Statut global

Les quatre versions prévues dans le brief initial (V1 plateau + IA, V2 analyse + exercices quotidiens, V3 coach réactif + programme pédagogique, V4 bibliothèque + progression persistante) sont livrées et fonctionnelles dans un seul fichier `index.html` autonome, gratuit, installable en PWA et testé (moteur de règles, IA, coach, bibliothèque de parties) à chaque étape plutôt qu'en apparence seulement.

## Architecture technique

- Un seul fichier HTML/CSS/JS (aucune dépendance, aucun build) → facile à héberger gratuitement n'importe où (GitHub Pages, Netlify, Vercel gratuit).
- Stockage prévu en V4 : IndexedDB (navigateur) — pas de serveur, pas d'abonnement.
- Aucune API payante, aucune clé requise.
