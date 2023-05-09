<script setup>
defineProps({
  titre: String,
  description: String,
  site: String
})
</script>

<template>
  <header>
    <h1>{{ titre }}</h1>
    <p class="description">{{ description }}</p>
    <a :href="site">
      <button>Site officiel</button>
    </a>
  </header>
</template>

<style scoped lang="css">
header {
  padding: 80px 0 20px;
  text-align: center;
}

header h1,
header .description {
  font-size: 3.25rem;
  color: white;
  text-shadow: 1px 1px 2px black; /* offset-x | offset-y | blur-radius | color */
}

header h1 {
  margin: 0;
}

header .description {
  font-size: 1.5rem;
  line-height: 1.25;
  max-width: 640px;
  margin: 0 auto 1em;
}
</style>
