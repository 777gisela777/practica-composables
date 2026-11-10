<template>
  <div class="disc">
    <img :src="img" class="img" />

    <h3>{{ title }}</h3>
    <div class="price">{{ price }} ¥</div>
    <button v-on:click="">View details</button>
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

<style scoped>
.card {
  background: #fff;
  padding: 1rem;
  border-radius: 14px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.08);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.thumb {
  width: 100%;
  border-radius: 10px;
}

.price {
  font-weight: bold;
  color: #2c7;
}

.description {
  font-size: 0.9rem;
  opacity: 0.8;
}
</style>
