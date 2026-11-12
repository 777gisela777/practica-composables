<template>
<NavigationBar />
<p v-if="loading">Loading...</p>
<p v-else-if="error">Error: {{ error }}</p>

<div v-else-if="data.meals" class="mealDetail">
  <div class="container-img">
    <img class="img" :src="data.meals[0].strMealThumb" :alt="data.meals[0].strMeal" />
  </div>
  <div class="mealInfo">
    <h3 class="name">{{ data.meals[0].strMeal }}</h3>
    <h4 class="country">{{ data.meals[0].strCountry }}</h4>
    <p class="instructions">{{ data.meals[0].strInstructions }}</p>
  </div>
</div>

<p v-else>Meal not found.</p>
</template>

<script setup>
import { watch } from 'vue';
import { useRoute } from 'vue-router';
import { useFetch } from '@/composables/useFetch.js';
import NavigationBar from '@/components/NavigationBar.vue';

const link = 'https://www.themealdb.com/api/json/v1/1/lookup.php?i=';

const route = useRoute();
const { data, error, loading, refetch } = useFetch(link + route.params.idMeal);

watch(() => route.params.idMeal, (newId) => refetch(link + newId));

defineProps({
  meal: Object,
  idMeal: Number,
  strMeal: String,
  strCategory: String,
  strArea: String,
  strCountry: String,
  strInstructions: String,
  strMealThumb: String
});
</script>
<style scoped>
.mealDetail {
  background: #fff;
  width: 80%;
  max-width: 900px;
  margin: 1.5rem auto;
  box-sizing: border-box;
  padding: 1rem;
  border-radius: 14px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.08);
  display: flex;
  align-items: center;
  gap: 1rem;
}

.img {
  display: block;
  width: 100%;
  height: auto;
  border-radius: 10px;
}

.container-img,
.mealInfo {
  width: 50%;
  min-width: 0;
}

.name {
  font-size: 1.5rem;
}

.country {
  font-weight: bold;
  font-size: 1.1rem;
  color: #3478f6;
}

.instructions {
  font-size: 1rem;
}

.error {
  color: red;
}

.container-img,
.mealInfo {
  width: 100%;
}
</style>
