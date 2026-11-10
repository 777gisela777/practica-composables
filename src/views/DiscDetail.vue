<template>
  <div class="disc">
    <img :src="img" class="img" />

    <h3>{{ title }}</h3>
    <div class="price">{{ price }} ¥</div>
    <div class="releaseDate">{{ releaseDate }}</div>
    <div class="description">{{ description }}</div>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  img: String,
  price: Number,
  releaseDate: String,
  description: String
});
</script>
