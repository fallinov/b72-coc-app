<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import { reactive, ref } from 'vue'
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
const troupes = reactive([
  {
    id: 1,
    nom: 'Barbare',
    description:
      'Ce guerrier intrépide compte sur ses muscles saillants et sa fière moustache pour semer le chaos dans les villages ennemis. Faites charger une horde de barbares et profitez du spectacle !',
    image: 'barbare.png',
    imageFond: 'barbare-bg.jpg',
    couleur: '#EC9B3B',
    niveau: 4,
    formation: 20,
    vitesse: 16,
    cout: 150
  },
  {
    id: 2,
    nom: 'Archer',
    description:
      "Ces tireurs d'élite préfèrent garder leurs distances, aussi bien sur le champs de bataille que dans la vie. Ils n'aiment rien tant que de voir tomber la cible sur laquelle ils ont jeté leur dévolu.",
    image: 'archer.png',
    imageFond: 'archer-bg.jpg',
    couleur: '#EE5487',
    niveau: 5,
    formation: 25,
    vitesse: 24,
    cout: 300
  },
  {
    id: 3,
    nom: 'Géant',
    description:
      "Ces grands gaillards semblent calmes de prime abord, mais ils se déchaîneront à la simple vue d'une tourelle ou d'un canon ! Lents mais résistants, ces guerriers sont faits pour encaisser les coups.",
    image: 'giant.png',
    imageFond: 'giant-bg.jpg',
    couleur: '#F6901A',
    niveau: 5,
    formation: 120,
    vitesse: 12,
    cout: 2250
  },
  {
    id: 4,
    nom: 'Gobelin',
    description:
      "Ces petites créatures agaçantes ne pensent qu'à une chose: le BUTIN ! Ils sont plus rapides qu'un piège à ressort, et leur appétit pour les ressources est sans limite.",
    image: 'goblin.png',
    imageFond: 'goblin-bg.jpg',
    couleur: '#82BB30',
    niveau: 5,
    formation: 30,
    vitesse: 32,
    cout: 100
  },
  {
    id: 5,
    nom: 'Dragon',
    description:
      "Les dragons sont connus à travers tout le territoire pour leur puissance sans égal. Cette terreur écailleuse du ciel ne montre aucune pitié ; et rien n'échappe à son souffle mortel.",
    image: 'dragon.png',
    imageFond: 'dragon-bg.jpg',
    couleur: '#5F3A59',
    niveau: 2,
    formation: 720,
    vitesse: 16,
    cout: 12000
  }
])

/* Méthodes */
function formerTroupe(cout) {
  if (totalOr.value < cout) {
    alert("Vous n'avez pas assez d'or mon seigneur !")
    return
  }
  totalOr.value -= cout
}
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
