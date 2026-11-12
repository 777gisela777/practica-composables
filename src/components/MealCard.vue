<template>
  <div class="mealCard">
    <img :src="meal.strMealThumb" :alt="meal.strMeal" class="img" />

    <h3 class="name">{{ meal.strMeal }}</h3>
    <RouterLink class="details-button" :to="{name:'Meal', params:{idMeal:meal.idMeal}}">View details</RouterLink>
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
.mealCard {
  background: #fff;
  padding: 1rem;
  border-radius: 14px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.08);
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin: 10px;
}

.img {
  width: 100%;
  border-radius: 10px;
}

.details-button {
  display: inline-block;
  width: fit-content;
  padding: 0.5rem 1rem;
  text-decoration: none;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-size: 14px;
  margin-bottom: 1rem;
  background: #3478f6;
  color: white;
  border-radius: 8px;
}

.details-button:hover {
    color: #fff;
    background-color: #224fa3;
}

</style>
