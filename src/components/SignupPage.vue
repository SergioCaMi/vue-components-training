<template>
  <div>
    <form @submit.prevent="signUp" novalidate action="">
      <label for="email1">Email</label>
      <input
        type="email"
        id="email1"
        name="email1"
        placeholder="Enter your email"
        required
        v-model="email"
        :style="{ borderColor: !validateForm ? 'transparent' : estateEmail === 0 ? 'red' : 'green' }"
      />
      <p class="msgEmail"><span v-if="validateForm && estateEmail === 1" class="icon success">✓</span> <span v-else-if="validateForm && estateEmail === 0" class="icon error">✗</span>{{ msg }}</p>

      <label for="password">Password</label>
      <input
        type="password"
        id="password"
        name="password"
        placeholder="Enter your password"
        required
        v-model="password"
        :style="{ borderColor: !validateForm ? 'transparent' : estatePass === 0 ? 'red' : 'green' }"
      />
      <p class="msgPass"><span v-if="validateForm && estatePass === 1" class="icon success">✓</span> <span v-else-if="validateForm && estatePass === 0" class="icon error">✗</span>{{ msgPass }}</p>

      <label for="nationality">Nationality</label>
      <select id="nationality" v-model="nationality" name="nationality" :style="{ borderColor: !validateForm ? 'transparent' : estateNationality === 0 ? 'red' : 'green' }" required>
        <option value="" selected>-- Elige una opción --</option>
        <option value="Hello">England</option>
        <option value="Hallo">Deutch</option>
        <option value="Bonjour">France</option>
      </select>
      <p class="msgNationality">
        <span v-if="validateForm && estateNationality === 1" class="icon success">✓</span> <span v-else-if="validateForm && estateNationality === 0" class="icon error">✗</span>{{ msgNationality }}
      </p>

      <button type="submit">Sign up</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";
const email = ref("");
const password = ref("");
const nationality = ref("");

const msg = ref("");
const estateEmail = ref(0);

const msgPass = ref("");
const estatePass = ref(0);

const msgNationality = ref("");
const estateNationality = ref(0);

const validateForm = ref(false);
const signUp = () => {
  validateForm.value = true;
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!emailRegex.test(email.value)) {
    msg.value = "No es un email valido";
    estateEmail.value = 0;
  } else {
    msg.value = "Es un email valido";
    estateEmail.value = 1;
  }

  let strength = 0;
  //  longitud
  if (password.value.length >= 8 && password.value.length <= 12) {
    strength++;
  }
  //  mayúscula
  if (/[A-Z]/.test(password.value)) {
    strength++;
  }
  //  número
  if (/\d/.test(password.value)) {
    strength++;
  }
  //  símbolo
  if (/[^A-Za-z0-9]/.test(password.value)) {
    strength++;
  }

  switch (strength) {
    case 1:
      msgPass.value = "The password is too weak";
      estatePass.value = 0;
      break;
    case 2:
      msgPass.value = "The password is weak";
      estatePass.value = 0;
      break;
    case 3:
      msgPass.value = "The password is moderate";
      estatePass.value = 1;
      break;
    case 4:
      msgPass.value = "The password is strong";
      estatePass.value = 1;
      break;
    default:
      msgPass.value = "The password is too weak";
      estatePass.value = 0;
  }

  if (nationality.value == "") {
    msgNationality.value = "TNationality NO";
    estateNationality.value = 0;
  } else {
    msgNationality.value = "OK";
    estateNationality.value = 1;
  }
};
</script>

<style scoped>
.icon.success {
  margin: 0 0.5rem;
  color: green;
  font-size: 18px;
}

.icon.error {
  margin: 0 0.5rem;
  color: red;
  font-size: 18px;
}
</style>
