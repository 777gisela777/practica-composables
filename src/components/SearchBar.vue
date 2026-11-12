<template>
    <div class="search-bar">
        <input
            v-model="query"
            type="text"
            placeholder="Search for a meal..."
            @keyup.enter="search"
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
<style scoped>
.search-bar {
    display: flex;
    flex-direction: row;
    gap: 1rem;
    justify-content: flex-end;
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    margin-right: 10px;
}

input {
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    border-radius: 3px;
    height: 30px;
    width: 200px;
    box-sizing: border-box;
    border: 1px solid #888;
}

input:focus {
    outline: none;
    border-color: #525252;
}

button {
    font-family:Verdana, Geneva, Tahoma, sans-serif;
    border-radius: 3px;
    background-color: #888;
    border: 1px solid;
    cursor: pointer;
    color: white;
}

button:hover {
    background-color: #707070;
}
</style>