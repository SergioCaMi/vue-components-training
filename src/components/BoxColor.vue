<template>
  <div :style="{ backgroundColor: stringRGB, color: textColor }">{{ stringRGB }} {{ rgbToHex }}</div>
</template>

<script setup>
import { computed } from "vue";
const props = defineProps({
  r: {
    type: Number,
    required: true,
    validator: (num) => num >= 0 && num <= 255,
  },
  g: {
    type: Number,
    required: true,
    validator: (num) => num >= 0 && num <= 255,
  },
  b: {
    type: Number,
    required: true,
    validator: (num) => num >= 0 && num <= 255,
  },
});

const stringRGB = computed(()=>{
  return `rgb(${props.r}, ${props.g}, ${props.b})`
})
const rgbToHex = computed(()=>{
  return "#" + props.r.toString(16).padStart(2, "0") + props.g.toString(16).padStart(2, "0") + props.b.toString(16).padStart(2, "0");
})


// Calculamos el color del texto contrastado
const textColor = computed(() => {
  // Fórmula ponderada simple para luminancia
  const luminance = (0.299 * props.r + 0.587 * props.g + 0.114 * props.b) / 255;
  // Si es más brillante que 0.5 → fondo claro → texto oscuro
  return luminance > 0.5 ? "black" : "white";
});


</script>

<style scoped>
div {
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
