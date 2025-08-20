<template>
  <div class="containerGrid">
    <div v-for="n in limit" :key="n" class="box" :class="n % 2 === 0 ? 'red' : 'white'">{{ n }}</div>
  </div>
</template>

<script setup>
const props = defineProps({
  limit: Number,
});
</script>

<style scoped>

div.containerGrid {
  display: grid;
  grid-template-columns: repeat(5, 60px);
}

.box {
  color: black;
  font-size: 30px;
  width: 60px;
  height: 60px;
  border: 2px solid black;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
.red {
  background-color: red;
}
.white {
  background-color: white;
}
</style>

