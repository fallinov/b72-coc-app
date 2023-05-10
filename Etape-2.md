# Étape 2
L'objectif est de découper le composant `src/App.vue` en plusieurs 
composants, afin d'en simplifier la compréhension et la maintenance.

A la fin de cette étape votre application devrait ressembler à ceci :
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

## Composant TopBarre

