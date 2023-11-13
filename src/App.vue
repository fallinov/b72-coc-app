<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {onMounted, reactive, ref} from 'vue'
// Importation des composants
import PageTopBarre from '@/components/PageTopBarre.vue'
import PageHeader from '@/components/PageHeader.vue'
import PageFooter from '@/components/PageFooter.vue'
import TroupeCarte from '@/components/TroupeCarte.vue'

/* Variables réactives */
const titre = ref('Clash of Clans')
const description = ref(`Construire un village,
                                former un clan et participer à des guerres de
                                clans épiques !`)
const site = ref('https://supercell.com/en/games/clashofclans/')
const totalOr = ref(20000)
const troupes = ref([])

/* Méthodes */
function formerTroupe(cout) {
  if (totalOr.value < cout) {
    alert("Vous n'avez pas assez d'or mon seigneur !")
    return
  }
  totalOr.value -= cout
}

// Quand le composant est monté, on va chercher les données
onMounted(() => {
  fetch('https://cocapi.divtec.me/troupes')
      .then((res) => res.json())
      .then((data) => {
        troupes.value = data
      })
})
</script>

<template>
  <page-top-barre :or="totalOr" />

  <page-header :titre="titre" :site="site" :description="description" />

  <main>
    <ul class="cartes">
      <li v-for="trp in troupes" :key="trp.id">
        <troupe-carte
            :troupe="trp"
            :or="totalOr"
            @former="formerTroupe"
        />
      </li>
    </ul>
  </main>

  <page-footer :site="site" />
</template>

<style scoped>
/*** Liste des cartes ***/
ul.cartes {
  list-style-type: none;
  padding: 0;
  margin: 2rem auto 80px;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 40px;
}

/*** Une carte ***/
ul.cartes li {
  margin: 40px 40px 80px;
  background: white;
  width: 300px;
  max-width: calc(100% - 80px);
  border-radius: 19px;
  position: relative;
  text-align: center;
  box-shadow: -1px 15px 30px -12px black;
  z-index: 99;
}
</style>
