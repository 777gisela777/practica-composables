<template>
    <div class="search-bar">
        <input
            v-model="query"
            type="text"
            placeholder="Search for a meal..."
        />
        <button @click="search">Search</button>
    </div>
</template>
<script setup>
import { ref } from 'vue';
const emit = defineEmits(['search']);
const query = ref('')

const search = () => {
    emit('search', query.value);
}
</script>