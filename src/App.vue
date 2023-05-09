<script setup>
// Cheat Sheet: https://steve-fallet.notion.site/Vue-3-script-setup-Cheat-Sheet-b12192ceae244ecda65f771579ca02bc
import {reactive, ref} from 'vue'

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
        description: 'Ce guerrier intrépide compte sur ses muscles saillants et sa fière moustache pour semer le chaos dans les villages ennemis. Faites charger une horde de barbares et profitez du spectacle !',
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
        description: 'Ces tireurs d\'élite préfèrent garder leurs distances, aussi bien sur le champs de bataille que dans la vie. Ils n\'aiment rien tant que de voir tomber la cible sur laquelle ils ont jeté leur dévolu.',
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
        description: 'Ces grands gaillards semblent calmes de prime abord, mais ils se déchaîneront à la simple vue d\'une tourelle ou d\'un canon ! Lents mais résistants, ces guerriers sont faits pour encaisser les coups.',
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
        description: 'Ces petites créatures agaçantes ne pensent qu\'à une chose: le BUTIN ! Ils sont plus rapides qu\'un piège à ressort, et leur appétit pour les ressources est sans limite.',
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
        description: 'Les dragons sont connus à travers tout le territoire pour leur puissance sans égal. Cette terreur écailleuse du ciel ne montre aucune pitié ; et rien n\'échappe à son souffle mortel.',
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
    if(totalOr.value < cout) {
        alert("Vous n'avez pas assez d'or mon seigneur !")
        return
    }
    totalOr.value -= cout
}
</script>

<template>
    <div class="solde-or">
        <img src="/img/piece-or-note.jpg" alt="Solde Or">
        {{ totalOr.toLocaleString('fr-CH') }}
        pièces d'or
    </div>
    <header>
        <h1>{{ titre }}</h1>
        <p class="description"> {{ description }}</p>
        <a :href="site">
            <button>Site officiel</button>
        </a>
    </header>
    <main>
        <ul class="cartes">
            <li v-for="troupe in troupes" :key="troupe.id">
                <article>
                    <header :style="`background: url('img/${ troupe.imageFond }')`">
                        <img :src="'img/' + troupe.image" :alt="troupe.nom"/>
                    </header>

                    <div class="level"
                         :style="`color: ${ troupe.couleur }`"
                    >
                        Niveau {{ troupe.niveau }}
                    </div>

                    <h2 class="name">{{ troupe.nom }}</h2>

                    <button :style="`background-color: ${ troupe.couleur }`"
                            @click="formerTroupe(troupe.cout)"
                            :disabled="totalOr < troupe.cout"
                    >
                        Former
                        <img src="/img/piece-or.png" alt="Former">
                    </button>

                    <p class="description">
                        {{ troupe.description }}
                    </p>

                    <footer >
                        <div class="training" :style="`background-color: ${ troupe.couleur }`">
                            <div v-if="troupe.formation > 60">
                                {{ Math.round(troupe.formation / 60) }}<sup>min
                            </sup>
                            </div>
                            <div v-else>
                                {{ troupe.formation }}<sup>sec</sup>
                            </div>
                            <div>Formation</div>
                        </div>

                        <div class="speed" :style="`background-color: ${ troupe.couleur }`">
                            <div>{{ troupe.vitesse }}</div>
                            <div>Vitesse</div>
                        </div>

                        <div class="cost" :style="`background-color: ${ troupe.couleur }`">
                            <div>{{ troupe.cout }}</div>
                            <div>Coût</div>
                        </div>
                    </footer>
                </article>
            </li>
        </ul>
    </main>
    <footer>
        &copy; 2023 - <a :href="site">Supercell.com</a>
    </footer>
</template>

<style scoped lang="sass">
/* https://sass-lang.com/guide */

</style>
