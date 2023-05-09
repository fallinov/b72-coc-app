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
