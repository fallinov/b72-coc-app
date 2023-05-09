# Clash of Clans App
Créer une application Vue à partir du site Clash of Clans (CoC) du contenu dans
le dossier `_sources/` de ce dépôt.

## Étape 1
Configuration du projet Vue et intégration de l'ancien site CoC

   * Installer les paquets 
      ```sh
      npm install
      ```
   * Ajouter le paquet pour Sass et SCSS
      ```sh
      npm install -D sass
      ```
   * Supprimer le fichier `src/assets/base.css`
   * Remplacer le fichier `src/assets/main.css`
     par celui du site CoC `css/main.css`
   * Copier le dossier `img/` du site CoC dans `public/`
   * Copier le fichier `favicon.ico` du site CoC dans `public/`
   * Modifier `App.vue` pour afficher la liste des cartes

## Commandes
### Installer les libraires
```sh
npm install
```
### Démarrer le serveur de développement
```sh
npm run dev
```
### Créer une version de production
```sh
npm run build
```
### Reformatter le code avec [Prettier](https://prettier.io/)
```sh
npm run format
```
### Analyser votre code avec with [ESLint](https://eslint.org/)
```sh
npm run lint
```
