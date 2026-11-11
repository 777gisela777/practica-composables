<template>
  <div class="mealCard">
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="meal.strMealThumb" />

    <h3>{{ meal.strMeal }}</h3>
    <RouterLink :to="{name:'Meal', params:{idMeal:meal.idMeal}}">View details</RouterLink>
  </div>
</template>

<script setup>
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

.details-button {
  display: inline-block;
  width: fit-content;
  padding: 0.5rem 1rem;
  color: white;
  background: #3478f6;
  border-radius: 6px;
  text-decoration: none;
}
</style>
