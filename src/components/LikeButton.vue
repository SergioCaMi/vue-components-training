<template>
  <div>
    <button @click="countLikes" :style="{ backgroundColor: color }">
      {{ counter }} Likes
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const colores = ['purple', 'blue', 'green', 'yellow', 'orange', 'red'];

const counter = ref(0);
const color = ref('gray'); 

const btnColor = () => {
  
  return colores[Math.floor(Math.random() * colores.length)];
};

const countLikes = () => {
  counter.value++;
  color.value = btnColor(); 
};</script>

<style scoped>
button {
    margin: 1rem;
    padding: 1rem 2rem;
    font-size: 30px;
}
</style>
