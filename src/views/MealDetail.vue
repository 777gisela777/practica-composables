<template>
<NavigationBar />
<p v-if="loading">Loading...</p>
<p v-else-if="error">Error: {{ error }}</p>

<div v-else-if="data.meals">
  <img :src="data.meals[0].strMealThumb" :alt="data.meals[0].strMeal" />
  <h3>{{ data.meals[0].strMeal }}</h3>
  <p>{{ data.meals[0].strInstructions }}</p>
</div>

<p v-else>Meal not found.</p>
</template>

<script setup>
import { watch } from 'vue';
import { useRoute } from 'vue-router';
import { useFetch } from '../composables/useFetch.js';
import NavigationBar from '@/components/NavigationBar.vue';

const link = 'https://www.themealdb.com/api/json/v1/1/lookup.php?i=';

const route = useRoute();
const { data, error, loading, refetch } = useFetch(`${link}${route.params.idMeal}`);

watch(() => route.params.idMeal, (newId) => refetch(`${link}${newId}`));

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
