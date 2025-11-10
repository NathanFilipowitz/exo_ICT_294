<script setup>
import {ref} from "vue";

const props = defineProps({
  details: {
    type: Boolean,
    required: true
  }
})
</script>

<template>
  <ul>
    <li v-for="detail in details">{{ detail }}</li>
  </ul>
</template>