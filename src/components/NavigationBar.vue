<template>
<nav>
    <RouterLink to="/" class="nav-link">Home</RouterLink>
</nav>
</template>
<script setup>
</script>
<style scoped>
nav {
    display: flex;
    flex-direction: row;
    margin: 10px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
}

.nav-link {
    padding: 8px 14px;
    border-radius: 8px;
    color: white;
    background-color: #3478f6;
    text-decoration: none;
}

.nav-link:hover {
    color: #fff;
    background-color: #224fa3;
}
</style>