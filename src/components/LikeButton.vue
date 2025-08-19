<template>
    <div>
        <button @click="countLikes">{{ counter }} Likes</button>
    </div>
</template>

<script setup>
import { ref } from 'vue';
</script>

<style scoped>

</style>