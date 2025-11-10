<script setup>
import { reactive } from 'vue'

const review = reactive({
  name: '',
  content: '',
  rating: null,
  user_recommend: null
})
const emit = defineEmits(['review-submitted'])
const onSubmit = () => {
  if (review.name === '' || review.content === '' || review.rating === null || review.user_recommend === null) {
    alert('Review is incomplete. Please fill out every field.')
    return
  }
  const productReview = {
    name: review.name,
    content: review.content,
    rating: review.rating,
    user_recommend: review.user_recommend
  }
  emit('review-submitted', productReview)
  // clear out the fields
  review.name = ''
  review.content = ''
  review.rating = null
  review.user_recommend = null
}

</script>

<template>
  <form class="review-form" @submit.prevent="onSubmit">
    <h3>Leave a review</h3>
    <label for="name">Name:</label>
    <input id="name" v-model="review.name">

    <label for="review">Review:</label>      
    <textarea id="review" v-model="review.content"></textarea>

    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="review.rating">
      <option>5</option>
      <option>4</option>
      <option>3</option>
      <option>2</option>
      <option>1</option>
    </select>
    <label>Would you recommend this product?</label>
    <input type="radio" id="recommend-yes" value="yes" v-model="review.user_recommend">
    <label for="recommend-yes">Yes</label>
    <input type="radio" id="recommend-no" value="no" v-model="review.user_recommend">
    <label for="recommend-no">No</label>

    <input class="button" type="submit" value="Submit">
  </form>
</template>