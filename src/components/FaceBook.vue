<template>
  <div v-for="profile in profiles" :key="profile.firstName" class="card">
    <div><img :src="profile.img" alt="Foto de perfil" /></div>
    <div class="data">
      <div><strong>First name:</strong> {{ profile.firstName }}</div>
      <div><strong>Last name:</strong> {{ profile.lastName }}</div>
      <div><strong>Country:</strong> {{ profile.country }}</div>
      <div><strong>Student:</strong> {{ profile.isStudent ? "Yes" : "No" }}</div>
    </div>
  </div>
</template>

<script setup>
import profiles from "../assets/data/berlin.json";
</script>

<style scoped>
.card {
  display: flex;
  margin: 1rem;
  border: 2px solid #ccc;
}

.data {
margin: 1rem;
}

img {
  margin: 1rem;
  width: 150px;
  object-fit: contain;
}
</style>
