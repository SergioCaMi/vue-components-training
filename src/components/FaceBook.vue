<template>
  <h2><strong>Profiles:</strong> {{ profiles.length }} {{ sortby }}</h2>
  <div class="options">
    <label for="ordenar">Sort by </label>
    <select id="ordenar" v-model="sortby">
      <option value="" default>---Choose an option---</option>
      <option value="firstName">First Name</option>
      <option value="lastName">Last Name</option>
      <option value="country">Country</option>
      <option value="isStudent">Type</option>
    </select>
    <label for="search"> Search </label>
    <input type="text" id="search" v-model="search" placeholder="text to find" />
  </div>
  <button class="countries" @click="selectedCountry = country" v-for="country in countries" :key="country">{{ country }}</button>
  <div
    v-for="profile in filterProfiles"
    :key="profile.lastName"
    class="card"
    :style="{ backgroundColor: selectedCountry === profile.country ? '#A3D2E2' : '', color: selectedCountry === profile.country ? 'black' : 'white' }"
  >
    <div><img @click="clickImage(profile.img)" :src="profile.img" alt="Foto de perfil" /></div>
    <div v-show="imgClick && selectedImage === profile.img" class="data">
      <div><strong>First name:</strong> {{ profile.firstName }}</div>
      <div><strong>Last name:</strong> {{ profile.lastName }}</div>
      <div><strong>Country:</strong> {{ profile.country }}</div>
      <div><strong>Type:</strong> {{ profile.isStudent ? "Student" : "Teacher" }}</div>
    </div>
  </div>
</template>

<script setup>
import profiles from "../assets/data/berlin.json";
import { ref, computed } from "vue";


const countries = [...new Set(profiles.map((profile) => profile.country))];
const selectedCountry = ref("");
const selectedImage = ref("");
const imgClick = ref(false);
const sortby = ref("");
const search = ref("");
const clickImage = (img) => {
  imgClick.value = !imgClick.value;
  selectedImage.value = img;
};

const filterProfiles = computed(() => {
  let result = [...profiles];

  if (sortby.value) {
    if (sortby.value == "firstName") result.sort((a, b) => a.firstName.localeCompare(b.firstName));
    if (sortby.value == "lastName") result.sort((a, b) => a.lastName.localeCompare(b.lastName));
    if (sortby.value == "country") result.sort((a, b) => a.country.localeCompare(b.country));
    if (sortby.value == "isStudent") result.sort((a, b) => Number(a.isStudent) - Number(b.isStudent));
  }

  if (search.value) {
    const query = search.value.toLowerCase();
    result = result.filter((profile) =>
      profile.firstName.toLowerCase().includes(query) || profile.lastName.toLowerCase().includes(query) ||
      profile.country.toLowerCase().includes(query)
    );
  }
  return result;
});
</script>

<style scoped>
.card {
  display: flex;
  margin: 1rem;
  border: 2px solid #ccc;
}

.data {
  margin: 1rem;
  color: ;
}

img {
  margin: 1rem;
  width: 150px;
  object-fit: contain;
}

.countries {
  margin: 0.1rem;
}

button {
  padding: 10px;
}

.options {
  margin: 0.1rem;
}

#ordenar {
  padding: 0.2rem;
}
</style>
