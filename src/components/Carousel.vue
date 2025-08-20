<template>
  <div class="container">
    <img :src="images[currentIndex]" alt="" />
    <div class="buttons">
      <button @click="prev"><<</button>
      <button @click="next">>></button>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
const props = defineProps({
  images: Array,
});
const currentIndex = ref(0);
const next = () => {
  currentIndex.value++;
  if (currentIndex.value == props.images.length) {
    currentIndex.value = 0;
  }
};
const prev = () => {
  currentIndex.value--;
  if (currentIndex.value < 0) {
    currentIndex.value = props.images.length - 1;
  }
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

img {
  width: 400px;
  object-fit: contain;
}

.buttons {
  display: flex;
}

button {
  padding: 1.5rem;
  margin: 1rem 3rem;
}
</style>
