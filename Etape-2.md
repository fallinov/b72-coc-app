# Étape 2
L'objectif est de découper le composant `src/App.vue` en plusieurs 
composants, afin d'en simplifier sa compréhension et sa maintenance.

À la fin de cette étape votre application devrait ressembler à ceci :


* `src/App.vue` : composant racine de l'application qui fera appel aux 
  composants suivants :
  * `src/components/PageTopBarre.vue` : composant pour la barre du solde d'or
  * `src/components/PageHeader.vue` : composant pour l'en-tête de la page
  * `src/components/PageFooter.vue` : composant pour le pied de page
  * `src/components/TroupeCarte.vue` : composant pour une troupe

## Suppression des composants inutiles
Avant de commencer, vous pouvez supprimer les composants suivants :
* `src/components/HelloWorld.vue`
* `src/components/TheWelcome.vue`
* `src/components/WelcomeItem.vue`

## Composant PageTopBarre
Le composant `PageTopBarre.vue` remplacera la `<div class="solde-or">` de `App.vue`.

`PageTopBarre.vue` affiche le solde d'or `totalOr` déclarer dans le composant `App.vue`.

Pour passer `totalOr` de `App.vue` à `PageTopBarre.vue`, il faut :

1. Définir une **propriété** dans`PageTobBarre.vue`.
2. Passer `totalOr` de `App.vue` via la propriété définie.

Ce passage de données via les _props_ est symbolisé par la flèche jaune dans le diagramme ci-dessous.

![6-coc-diagramme-pageTopBarre.png](_medias%2F6-coc-diagramme-pageTopBarre.png)

### Instructions
1. Créez le composant `src/components/PageTopBarre.vue`
2. Ajouter l'élément HTML `<div class="solde-or">` du composant `src/App.vue` au `<template>` de `PageTopBarre.vue`.
3. Pour que `App.vue` puisse passer `totalOr` à `PageTobBarre.vue`, définir une **propriété `or`**
   dans `PageTobBarre.vue`.
   La propriété `or` est **obligatoire** et doit être de **type `Number`**.
    ```vue
   <script setup>
    defineProps({
        or: {
            type: Number,
            required: true
        }
    })
    </script>
    ```
4. Ajouter le composant `PageTopBarre.vue` dans `App.vue` à la place de `<div class="solde-or">` 
   et lui passer `totalOr` de `App.vue` via la propriété `or`.
    ```vue
    <page-top-barre :or="totalOr" />
    ```
5. Importer le style CSS de `src/assets/main.css` qui concerne `.solde-or`
   dans `<style>` de `PageTopBarre.vue` et le réécrire en **Sass** ou en **SCSS**.
    ```vue
    <style scoped lang="sass">
    .solde-or
        position: fixed
        width: 100%
        background: white
        color: #3B3B3B
        padding: .5rem
        height: 60px
        z-index: 9999
        box-shadow: rgba(0, 0, 0, 0.25) 0 8px 15px
        
    .solde-or img
        max-height: 3em
        vertical-align: middle
    </style>
    ```
   
## Composant PageHeader
Le composant `PageHeader.vue` remplacera la `<header>` de `App.vue`.



