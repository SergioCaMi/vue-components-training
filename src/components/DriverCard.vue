<template>
  <div class="card">
    <img :src="img" alt="" />
    <div class="data">
      <h2>{{ name }}</h2>
      <p>
        <span class="filled" v-for="r in fillStarts">★</span>
        <span class="empty" v-for="r in emptyStarts">☆</span>
      </p>
      <p>{{ car.model }} - {{ car.licensePlate }}</p>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";



const props = defineProps({
  name: String,
  rating: Number,
  img: String,
  car: Object
});

const fillStarts = computed(() => {
  return Math.round(props.rating);
});

const emptyStarts = computed(() => {
  return 5 - fillStarts.value;
});
</script>

<style scoped>
.card {
  display: flex;
  margin: 2rem;
  align-items: center;
  justify-content: center;
  color: white;
  background-color: #455eb5;
  border-radius: 15px;
}

.card img {
  margin: 2rem;
  width: 150px;
  height: 150px;
  border-radius: 100%;
}

.filled {
  color: white;
}

.empty {
  color: #ccc;
}
</style>
