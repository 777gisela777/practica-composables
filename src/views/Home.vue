<template>
  <NavigationBar />
  <h1>Desserts</h1>
  <SearchBar @search="searchMeals" />
  <div>
    <!--button @click="fetchData" class="refresh">Torna a carregar</button-->
    <button @click="refetch()" class="refresh">Refresh</button>

    <div v-if="loading" class="center">Loading...</div>
    <div v-else-if="error" class="center error">Error: {{ error }}</div>

    <div v-else class="grid">
      <MealCard
        v-for="m in data.meals"
        :key="m.idMeal"
        :meal="m"
      />
    </div>
  </div>
</template>

<script setup>
import NavigationBar from '@/components/NavigationBar.vue';
import MealCard from '../components/MealCard.vue';
import { useFetch } from '../composables/useFetch.js';
import SearchBar from '@/components/SearchBar.vue';
const { data, error, loading, refetch } = useFetch('https://www.themealdb.com/api/json/v1/1/filter.php?c=Dessert');
//const { data, error, loading, fetchData } = useFetch('www.themealdb.com/api/json/v1/1/filter.php?c=Dessert');

async function searchMeals(input) {
  const url = 'https://www.themealdb.com/api/json/v1/1/search.php?s=' + encodeURIComponent(input);
  await refetch(url);
  if (data.value.meals) {
    data.value.meals = data.value.meals.filter((meal) => meal.strCategory === 'Dessert');
  }
}
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
  margin-left: 10px;
  text-decoration: none;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 14px;
  border: 1px solid;
  cursor: pointer;
}

.refresh:hover {
    color: #fff;
    background-color: #224fa3;
}

.center {
  text-align: center;
  padding: 2rem;
}

.error {
  color: red;
}

h1 {
  display: flex;
  justify-content: center;
}
</style>
