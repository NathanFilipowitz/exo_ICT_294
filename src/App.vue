<script setup>
import { ref } from "vue"; //définit l'élément comme réactif (ici, unidirectionnel)

const product = ref("boots");
const description = ref("ceci est ma description");
</script>

<template>
    <h1>{{ product }}</h1>
    <p>{{ description }}</p>
</template>
