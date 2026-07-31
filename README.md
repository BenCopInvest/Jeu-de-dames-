# Damier — Entraîneur de Dames Internationales (V1)

Application 100 % gratuite, jouable hors ligne, sans compte ni carte bancaire.

## Ce que contient cette V1

- Plateau 10×10 tactile (portrait/paysage automatique), zoom fluide sur mobile.
- Moteur de règles FMJD complet : prise obligatoire, **prise maximale**, dames volantes (longue portée), promotion.
- Mode Joueur contre Joueur et mode contre IA (5 niveaux : débutant → expert), moteur minimax + élagage alpha-bêta.
- Panneau « Coach virtuel » : questions socratiques avant de jouer (centre, menaces, coups candidats, plan) + bouton d'analyse de position.
- Historique des coups, compteur de prises/coups, annulation.
- Fonctionne 100 % hors ligne une fois ouverte une première fois (aucun appel réseau dans le jeu).

## Limitation connue de cette version

Pour rester simple en V1, la promotion en dame pendant une **rafle multiple** n'est appliquée qu'à la toute fin de la séquence de prises (et non au milieu, comme l'exige strictement la règle FMJD dans de rares positions). Cela n'affecte qu'un petit nombre de positions de rafle avancées — à corriger en V2.

## Installer comme application (PWA) — gratuit, sans magasin d'applications

1. Créez un dépôt GitHub public et déposez les 3 fichiers (`index.html`, `manifest.json`, `sw.js`).
2. Activez **GitHub Pages** (Settings → Pages → Deploy from branch → `main` / racine). C'est gratuit, sans carte bancaire.
3. Ouvrez l'URL fournie par GitHub Pages sur le téléphone :
   - **Android (Chrome)** : menu ⋮ → « Ajouter à l'écran d'accueil ».
   - **iPhone (Safari)** : bouton Partager → « Sur l'écran d'accueil ».
4. L'icône apparaît comme une application native ; elle fonctionne ensuite hors ligne.

Alternative sans GitHub : Netlify Drop (netlify.com/drop) — glisser le dossier, gratuit, aucune carte bancaire.

## Feuille de route (comme demandé dans le brief)

**V2 — Analyse & entraînement**
- Rapport après partie (erreurs critiques, coups manqués, Elo estimé).
- Générateur d'exercices tactiques quotidiens (5 tactiques + 1 position stratégique/jour).
- Corriger la promotion en cours de rafle (règle FMJD stricte).

**V3 — Coach intelligent & pédagogie**
- Parcours de cours structuré (centre, chaînes de pions, Roozenburg, Keller, tenaille, sacrifices).
- Le coach commente réellement le coup joué (pas seulement des questions génériques) via une petite bibliothèque de motifs tactiques détectés automatiquement.

**V4 — Bibliothèque & progression**
- Base de parties historiques et finales théoriques annotées.
- Tableau de bord Elo/progression persistant (stockage local IndexedDB), synchronisation optionnelle.

## Architecture technique

- Un seul fichier HTML/CSS/JS (aucune dépendance, aucun build) → facile à héberger gratuitement n'importe où (GitHub Pages, Netlify, Vercel gratuit).
- Stockage prévu en V4 : IndexedDB (navigateur) — pas de serveur, pas d'abonnement.
- Aucune API payante, aucune clé requise.
- 
