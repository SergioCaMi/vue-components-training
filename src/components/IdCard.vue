<template>
  <div class="card">
    <div><img :src="picture" alt="Foto de perfil" /></div>
    <div>
        <div><strong>First name:</strong> {{ firstName }}</div>
        <div><strong>Last name:</strong> {{ lastName }}</div>
        <p><strong>Gender:</strong> {{ gender }}</p>
        <p><strong>Height:</strong> {{ height/100 }} m</p>
        <p><strong>Birth:</strong> {{ birth.toDateString() }}</p>
    </div>
  </div>
</template>
<script setup>
defineProps({
  lastName: String,
  firstName: String,
  gender: {
    type: String,
    validator: (value) => ["male", "female"].includes(value),//función!
  },
  height: Number,
  birth: Date,
  picture: String,
});
</script>
<style scoped>
.card {
    margin: 1rem;
    display: flex;
    padding: 1rem;
    border: 1px solid #ccc;
}

.card img {
    margin: 0 1rem;
}
</style>
