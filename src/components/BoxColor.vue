<template>
<div :style="{ backgroundColor: `rgb(${r}, ${g}, ${b})`, color: textColor}">
rgb({{ r }}, {{ g }}, {{ b }}) {{ rgbToHex(r, g, b) }}
</div></template>

<script setup>
import { computed } from 'vue'

// Calculamos el color del texto contrastado
const textColor = computed(() => {
  // Fórmula ponderada simple para luminancia 
  const luminance = (0.299 * props.r + 0.587 * props.g + 0.114 * props.b) / 255;
  // Si es más brillante que 0.5 → fondo claro → texto oscuro
  return luminance > 0.5 ? 'black' : 'white';
});

//Valor rgb a hexadecimal
const rgbToHex = (r, g, b) => {
  return '#' + 
    r.toString(16).padStart(2, '0') +
    g.toString(16).padStart(2, '0') +
    b.toString(16).padStart(2, '0');
};

const props = defineProps({
  r: {
    type: Number,
    required: true,
    validator: num => num >= 0 && num <= 255
  },  
  g: {
    type: Number,
    required: true,
    validator: num => num >= 0 && num <= 255
  },  
  b: {
    type: Number,
    required: true,
    validator: num => num >= 0 && num <= 255
  },
})

</script>

<style scoped>
div {
    color: #ccc;
    font-size: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 1rem;
    border: 2px solid black;
    width: 600px;
    height: 200px;
}
</style>
