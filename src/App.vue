<script setup>
import { ref } from 'vue'
import ProductDisplay from '@/components/ProductDisplay.vue'

const cart = ref([])
const premium = ref(true)

const addToCart = (id) => {
  cart.value.push(id)
}
const removeFromCart = (id) => {
  const item = cart.value.indexOf(id) //recherche de la position de l'item dans le panier
  if (item >= 0) { //vérification de la présence de l'item dans le panier
    cart.value.splice(item, 1)
  }
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart.length }})</div>
  <ProductDisplay :premium="premium" @add-to-cart="addToCart" @remove-from-cart="removeFromCart"></ProductDisplay>
</template>