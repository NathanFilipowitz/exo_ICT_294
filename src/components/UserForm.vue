<script setup>
import { reactive } from 'vue'


function getEmojiByMood(mood) {
    let emojis = [ "😤","😢", "😖", "😟", "😒", "😐", "😊", "😃", "😁", "😆"] // la touche windows + "." permettent de choisir des emojis
    let index = Math.floor(mood / 10) - 1;
    if (index === -1) index = 0;
    return emojis[index];
}

const userInscription = reactive({
    lastname: '',
    firstname: '',
    description: '',
    sex: null,
    hobbys: [],
    birthdate: '',
    mood: null
})
const emit = defineEmits(['inscription-submitted'])
const onSubmit = () => {
    // ensure user enters informations for all fields
    if (userInscription.lastname === '' || userInscription.firstname === '' || userInscription.description === '' || userInscription.sex === null || userInscription.hobbys.length === 0 || userInscription.birthdate === null || userInscription.mood === null) {
        alert('Inscription is incomplete. Please fill out every field.')
        return
    }
    const inscription = {
        firstname: userInscription.firstname,
        lastname: userInscription.lastname,
        description: userInscription.description,
        sex: userInscription.sex,
        hobbys: userInscription.hobbys,
        birthdate: userInscription.birthdate,
        mood: userInscription.mood
    }
    emit('inscription-submitted', inscription)
    // clear out the fields
    userInscription.firstname = ''
    userInscription.lastname = ''
    userInscription.description = ''
    userInscription.sex = null
    userInscription.hobbys = []
    userInscription.birthdate = null
    userInscription.mood = null
}

</script>

<template>
    <form class="inscription-form" @submit.prevent="onSubmit">
        <h1>Formulaire d'inscription</h1>
        <label for="lastname">Lastname :</label>
        <input id="lastname" v-model="userInscription.lastname">

        <label for="firstname">Firstname :</label>
        <input id="firstname" v-model="userInscription.firstname">

        <label for="description">Description :</label>
        <textarea id="description" v-model="userInscription.description"></textarea>

        <label>Sexe : </label>
        <div class="options-group">
            <label>Male
                <input type="radio" id="sex-male" value="male" v-model="userInscription.sex">
            </label>
            <label>Female
                <input type="radio" id="sex-female" value="female" v-model="userInscription.sex">
            </label>
            <label>Other
                <input type="radio" id="sex-other" value="other" v-model="userInscription.sex">
            </label>
        </div>

        <label>Hobbies : </label>
        <div class="options-group">
            <label for="hobby-sport">Sport :
                <input type="checkbox" id="hobby-sport" value="sport" v-model="userInscription.hobbys">
            </label>
            <label for="hobby-environment">Environnement :
                <input type="checkbox" id="hobby-environment" value="environment" v-model="userInscription.hobbys">
            </label>
        </div>

        <label for="birthdate">Birthdate :</label>
        <input type="date" id="birthdate" v-model="userInscription.birthdate">

        <label for="mood">Mood :</label>
        <div id="mood-slider">
            <input type="range" min="10" max="100" step="10" class="slider" v-model.number="userInscription.mood">
        </div>
        <label class="emoji-label">{{ getEmojiByMood(userInscription.mood) }}</label>

        <input class="button" type="submit" value="Submit">

    </form>
</template>

<style scoped>
.emoji-label {
    font-size: 50px;
    justify-content: start; /* Center the emoji horizontally */
}
</style>