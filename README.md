# Dar Salma – Application de gestion

Application de gestion de la maison d'hôtes Dar Salma : réservations, calendrier des 6 chambres et du studio, clients, paiements, dépenses et ménage. Elle fonctionne sur téléphone et sur PC, et les données sont partagées en temps réel.

Ce projet est indépendant de M&T HACCP : dépôt séparé, base de données séparée.

## Contenu du dossier

| Fichier | Rôle |
|---|---|
| `index.html` | L'application |
| `firebase-config.js` | La clé de connexion à votre base Firebase (à remplir) |
| `firestore.rules` | Les règles de sécurité : qui a le droit de voir les données |
| `manifest.webmanifest`, `icon-*.png`, `logo.webp` | Logo et icône pour « Ajouter à l'écran d'accueil » |

## Étape 1 – Créer la base Firebase (gratuit)

1. Allez sur https://console.firebase.google.com et connectez-vous avec un compte Google.
2. Cliquez sur **Créer un projet** et nommez-le `dar-salma`. Google Analytics n'est pas nécessaire.
3. Dans le menu de gauche, ouvrez **Build › Authentication**, cliquez sur **Commencer**, puis activez **Adresse e-mail/Mot de passe**.
4. Toujours dans Authentication, onglet **Utilisateurs**, cliquez sur **Ajouter un utilisateur**. Créez votre compte, puis celui de votre mère (e-mail et mot de passe).
5. Ouvrez **Build › Firestore Database**, cliquez sur **Créer une base de données**, choisissez l'emplacement **europe-west** et le **mode production**.
6. Dans Firestore, onglet **Règles** : collez le contenu de `firestore.rules`, remplacez les deux adresses e-mail par les vôtres, puis cliquez sur **Publier**.
7. Cliquez sur la roue dentée › **Paramètres du projet** › **Vos applications** › icône **</>** (Web). Nommez l'application `Dar Salma` et ne cochez pas « Hosting ». Copiez le bloc `firebaseConfig` affiché et collez ses valeurs dans `firebase-config.js`.

## Étape 2 – Mettre l'application en ligne (GitHub Pages)

1. Sur GitHub, créez un nouveau dépôt **public** nommé `dar-salma`.
2. Envoyez-y tous les fichiers de ce dossier.
3. Dans le dépôt : **Settings › Pages** › Source : **Deploy from a branch**, branche `main`, dossier `/ (root)`, puis **Save**.
4. Après une minute, l'adresse s'affiche, par exemple `https://VOTRE-COMPTE.github.io/dar-salma/`.
5. Retournez dans Firebase › **Authentication › Paramètres › Domaines autorisés** et ajoutez `VOTRE-COMPTE.github.io`.

## Étape 3 – Utilisation

- Ouvrez l'adresse et connectez-vous avec l'e-mail et le mot de passe créés à l'étape 1.
- À la première connexion, les 6 chambres et le studio sont créés automatiquement. Les prix et les détails se modifient dans **Finances › Chambres**.
- **Sur téléphone** : dans le menu du navigateur, choisissez **Ajouter à l'écran d'accueil** (sur iPhone : bouton Partager puis « Sur l'écran d'accueil »). L'application s'ouvre ensuite comme une vraie appli, avec le logo.
- **Mot de passe oublié** : le lien sur l'écran de connexion envoie un e-mail de réinitialisation.

## Sécurité

- Seules les adresses e-mail listées dans les règles Firestore peuvent lire ou modifier les données, même si quelqu'un trouve l'adresse du site.
- La clé dans `firebase-config.js` peut être publique : c'est normal pour Firebase. La protection vient des règles et des comptes.
- L'offre gratuite de Firebase (plan Spark) suffit largement pour une maison d'hôtes.
