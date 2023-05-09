<script setup>
defineProps({
  or: {
    type: Number,
    required: true
  }
})
</script>

<template>
  <div class="solde-or">
    <img src="/img/piece-or-note.jpg" alt="Solde Or" />
    {{ or.toLocaleString('fr-CH') }}
    pièces d'or
  </div>
</template>

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
