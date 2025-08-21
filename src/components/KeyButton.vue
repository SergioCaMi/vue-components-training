<script setup>

// Defines los eventos que el componente puede emitir a su padre
defineEmits({
    press: String // nombre del evento : tipo de dato que va a enviar
})

defineProps({
    label: String
})

</script>

<template>
    <button class="key" @click="$emit('press', label)"> {{ label }}</button>
</template>

<style scoped>
.key {
  width: 60px;
  height: 60px;
  font-size: 24px;
  font-weight: bold;
  border: none;
  border-radius: 8px;
  background: linear-gradient(145deg, #f0f0f0, #d9d9d9);
  box-shadow: 3px 3px 6px #aaa, -2px -2px 5px #fff;
  cursor: pointer;
  transition: all 0.1s ease-in-out;
}
.key:active {
  box-shadow: inset 3px 3px 6px #aaa, inset -2px -2px 5px #fff;
  transform: translateY(2px);
  background: linear-gradient(145deg, #e0e0e0, #cfcfcf);
}
</style>