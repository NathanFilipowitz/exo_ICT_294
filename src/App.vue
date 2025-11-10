<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'
import ProductDetails from "@/components/ProductDetails.vue";

const cart = ref(0)
const premium = ref(true)
const details = ref(['50% cotton', '30% wool', '20% polyester'])

</script>
  
<template>
  <div id="app">
    <div class="nav-bar"></div>

    <div class="cart">Cart({{ cart }})</div>
    <ProductDisplay :premium="premium" ></ProductDisplay>
    <ProductDetails :details="details" ></ProductDetails>

  </div>
</template>