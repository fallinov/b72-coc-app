# Étape 1
Configuration de l'application Vue et intégration de l'ancien site CoC

## 1. Configuration du projet
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
     ![1-vue-app-base.png](_medias%2F1-vue-app-base.png)
---
## 2. Titre du site, CSS et images
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
     ![2-coc-avec-css.png](_medias%2F2-coc-avec-css.png)

## 3. Page d'accueil de base
Remplacer le contenu de `src/App.vue` par le code ci-dessous.
```vue
<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {reactive, ref} from 'vue'

// Variable réactive primitive avec une valeur simple
const titre = ref('Clash of Clans')
// Variable réactive complexe avec plusieurs propriétés
const troupes = reactive(['Barbare', 'Archer', 'Géant'])
</script>

<template>
  <h1>{{ titre }}</h1>
  <ul>
    <li v-for="troupe in troupes" :key="troupe">
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
  ![3-coc-app-base.png](_medias%2F3-coc-app-base.png)
---

## 4. Intégration du site CoC
Intégrer dans `src/App.vue` les contenus des fichiers `index.html` et 
`js/main.js` du site CoC.
1. Commenter ou supprimer le contenu du `<style>` de `src/App.vue`
2. Copier le contenu de `<div id="app">` du fichier `index.html` du site CoC
  dans le `<template>` de `src/App.vue`
2. Copier et réécrire le contenu du fichier `js/main.js` du site CoC dans  
   `<script setup>` de `src/App.vue` en utilisant la composition API de Vue 3.
   [Vue 3 "script setup" Cheat Sheet](https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc)
![4-coc-integration.png](_medias%2F4-coc-integration.png)
---
