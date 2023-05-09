# Clash of Clans App
Créer une application Vue à partir du site Clash of Clans (CoC) du contenu dans
le dossier `_sources/` de ce dépôt.

## Étape 1
Configuration du projet Vue et intégration de l'ancien site CoC
### Configuration du projet

   * Installer les paquets 
      ```sh
      npm install
      ```
   * Ajouter le paquet pour Sass et SCSS
      ```sh
      npm install -D sass
      ```
   * Démarrer le serveur de développement
      ```sh
      npm run dev
      ```
### Intégration du site CoC
   * Changer le titre de la page, de l'application, dans `src/index.html`
     ```html 
     <!-- Ancienne valeur -->
     <title>Vite App</title>
     <!-- Nouvelle valeur -->
     <title>Clash of Clans</title>
     ```
   * Supprimer le fichier `src/assets/base.css`
   * Remplacer le fichier `src/assets/main.css`
     par celui du site CoC `css/main.css`
   * Copier le dossier `img/` du site CoC dans `public/`
   * Remplacer le fichier `public/favicon.ico` par celui du site CoC
   * Remplacer le contenu de `src/App.vue` par le code ci-après
     ```vue
     <script setup>
     // Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
     import {reactive, ref} from 'vue'
     const titre = ref('Clash of Clans')
     const troupes = reactive(['Barbare', 'Archer', 'Géant'])
     </script>
     
     <h1>{{ titre }}</h1>
     <template>
       <ul>
         <li v-for="troupe in troupes" :key="troupe.id">
           {{ troupe }}
         </li>
       </ul>
     </template>
     
     <style scoped lang="sass">
     /* https://sass-lang.com/guide */
     $primary: #800080
     $secondary: #fefefe
     
     h1
       color: $primary
       text-align: center
     
     ul
       list-style: none
       display: flex
       flex-wrap: wrap
       justify-content: center
       li
         color: $secondary
         background-color: $primary
         margin: 1rem
         padding: 1rem
         max-width: 200px
     </style>
     
     ```

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
