<template>
  <div id="container">
    <div class="colorBox" :style="{ backgroundColor: `rgb(${props.color === 'r' ? props.value : 0}, ${props.color === 'g' ? props.value : 0}, ${props.color === 'b' ? props.value : 0})` }"></div>
    <label for="inputColor">{{ props.color.toUpperCase() }}</label>
    <input id="inputColor" type="number" :value="props.value" @input="$emit('change', Number($event.target.value))" :min="0" :max="255" step="1" />
  </div>
</template>

<script setup>
const props = defineProps({
  color: String,
  value: Number,
//   onchange: Function,
});

defineEmits({
  change: Number,
});

</script>

<style scoped>
#container {
  display: flex;
  align-items: center;
}
#inputColor {
  width: 100px;
  height: 50px;
}
.colorBox {
  margin: 0 0.5rem;
  width: 50px;
  height: 50px;
  border: 2px solid black;
}
label {
  height: 50px;
  margin: 0 0.5rem;
}
</style>
