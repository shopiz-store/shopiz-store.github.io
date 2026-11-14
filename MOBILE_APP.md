# SHOPIZ — Android et iPhone

Ce dépôt contient désormais une base **Capacitor** pour créer des applications natives Android et iOS à partir du catalogue SHOPIZ. Le site GitHub Pages continue à fonctionner indépendamment.

## Prérequis

- Node.js 20+ et npm
- Android Studio et Android SDK pour Android
- macOS + Xcode pour compiler et publier sur iOS
- Comptes développeurs Google Play et Apple Developer pour distribuer sur les stores

## Préparer et ouvrir Android

```bash
npm install
npm run mobile:prepare
npx cap add android
npm run mobile:sync
npx cap open android
```

Dans Android Studio, tester sur un appareil ou un émulateur, puis générer un **Android App Bundle (.aab)** signé pour Google Play.

## Préparer et ouvrir iOS (Mac obligatoire)

```bash
npm install
npm run mobile:prepare
npx cap add ios
npm run mobile:sync
npx cap open ios
```

Dans Xcode, sélectionner l'équipe Apple Developer, configurer la signature, tester sur iPhone et archiver l'application pour App Store Connect.

## Points importants avant toute publication

1. **Le code source n'est pas une application publiée** : Android/iOS ne sont pas encore compilés, signés ni testés. Les dossiers natifs seront générés avec `cap add`.
2. **Vérifier Amazon Partenaires** : l'usage des liens d'affiliation dans une application mobile peut nécessiter des conditions ou autorisations spécifiques. Ne pas supposer que l'agrément du site couvre automatiquement l'application.
3. **App Store** : Apple peut rejeter une simple version encapsulée du site. Prévoir des fonctionnalités mobiles originales et une expérience réellement utile.
4. **Confidentialité** : publier une politique de confidentialité complète, décrire Supabase Auth, les données traitées et les modalités de suppression de compte. Fournir un parcours de suppression de compte dans l'application si requis.
5. **Authentification** : tester les redirections e-mail Supabase (confirmation et réinitialisation), qui utilisent actuellement l'adresse du site web. Prévoir des liens profonds mobiles avant la mise en production.
6. **Liens Amazon** : tester l'ouverture hors application et le suivi affilié. Vérifier les références produits, prix et images avant publication.
7. **Visuels** : fournir des icônes PNG adaptatives 512×512 et les icônes iOS requises, ainsi que captures d'écran des appareils demandés par les stores. L'icône SVG actuelle est une base visuelle, pas le jeu complet d'assets natifs.
8. **Tests et conformité** : vérifier sécurité, accessibilité, navigation, permissions, politique de confidentialité, règles Google Play et Apple App Review.

## Mise à jour du catalogue

Après toute modification du `index.html` racine :

```bash
npm run mobile:sync
```

Le dossier `www/` est généré depuis les fichiers du site et ignoré par Git. Ne pas le modifier manuellement.
