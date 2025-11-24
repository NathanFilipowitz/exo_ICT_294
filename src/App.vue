<script setup>
import { ref } from "vue";
import socksGreenImage from "./assets/images/socks_green.jpeg";

const product = ref("Socks");
const image = ref(socksGreenImage);
const inventory = ref(100);
const onSale = ref(true);
</script>

<template>
    <div class="nav-bar"></div>
    <div class="product-display">
        <div class="product-container">
            <div class="product-image">
                <img v-bind:src="image" />
            </div>
            <div class="product-info">
                <h1>{{ product }}</h1>
            </div>
            <p v-if="inventory > 30">In Stock</p>
<!--          utiliser v-if plutot que v-show car v-show ne fait que d'appliquer display=none (donc enft tjr présent sur le navigateur)-->
            <p v-else-if="inventory <= 30 && inventory > 0">
                Almost sold out !
            </p>
            <p v-else>Out of Stock</p>
            <p v-if="onSale">On Sale !!</p>
        </div>
    </div>
</template>
