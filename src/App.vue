<script setup>
import { ref } from "vue";
import socksGreenImage from "./assets/images/socks_green.jpeg";

const product = ref("Socks");
const image = ref(socksGreenImage);
const url = ref(
    "https://www.vuemastery.com/courses/intro-to-vue-3-comp-api/attribute-binding-comp-api",
);
const urlText = ref("Guide suivi");
</script>

<template>
    <div class="product-display">
        <div class="product-container">
            <div class="product-image">
                <img v-bind:src="image" />
            </div>
            <div class="product-info">
                <h1>{{ product }}</h1>
            </div>
            <a :href="url" v-text="urlText"></a>
        </div>
    </div>
</template>
