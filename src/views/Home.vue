<template>
  <div>
    <!--button @click="fetchData" class="refresh">Torna a carregar</button-->
    <button @click="refetch" class="refresh">Refresh</button>

    <div v-if="loading" class="center">Loading...</div>
    <div v-else-if="error" class="center error">Error: {{ error }}</div>

    <div v-else class="grid">
      <DiscCard
        v-for="d in data.discs"
        :key="d.id"
        :title="d.title"
        :price="d.price"
        :releaseDate="d.releaseDate"
        :description="d.description"
        :img="d.img"
      />
    </div>
  </div>
</template>

<script setup>
import ProductCard from './ProductCard.vue';
import { useFetch } from '../composables/useFetch.js';
const { data, error, loading, refetch } = useFetch('https://dummyjson.com/products');
//const { data, error, loading, fetchData } = useFetch('https://dummyjson.com/products');
</script>

<style scoped>
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(230px, 1fr));
  gap: 1rem;
}

.refresh {
  margin-bottom: 1rem;
  padding: 0.5rem 1rem;
  background: #3478f6;
  color: white;
  border-radius: 8px;
}

.center {
  text-align: center;
  padding: 2rem;
}

.error {
  color: red;
}
</style>
