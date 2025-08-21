<template>
    
  <div>
    <form @submit.prevent="signUp" action="">
      <label for="email1">Email</label>
      <input type="email" id="email1" name="email1" placeholder="Enter your email" required v-model="email"/>
      <p class="msgEmail"></p>
      <label for="password">Password</label>
      <input type="password" id="password" name="password" placeholder="Enter your password" required v-model="password"/>
      <p class="msgPass"></p>
      <label for="nationality">Nationality</label>
      <select id="nationality" v-model="nationality" name="nationality" required >
        <option value="" selected>-- Elige una opción --</option>
        <option value="Hello">England</option>
        <option value="Hallo">Deutch</option>
        <option value="Bonjour">France</option>
      </select>
      <p>{{ nationality }}</p>
      <p>{{ email }}</p>
      <p>{{ email }} - {{ password }} - {{ nationality }}</p>
      <button type="submit">Sign up</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
const email = ref("");
const password = ref("");
const nationality = ref("");
const signUp = ()=>{

}
</script>

<style scoped>

</style>
