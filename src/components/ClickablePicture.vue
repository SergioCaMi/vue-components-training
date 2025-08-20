<template>
  <div>
    <img @click="toggleIMG" :src="image" alt="" />
  </div>
</template>

<script setup>
import { ref } from "vue";
import marceIMG from "/maxence.png";
import marceGlassesIMG from "/maxence-glasses.png";

const image = ref(marceIMG);
const toggleIMG = () => {
  image.value = image.value === marceIMG ? marceGlassesIMG : marceIMG;
};
</script>

<style scoped></style>
