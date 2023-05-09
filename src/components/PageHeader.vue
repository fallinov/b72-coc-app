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
