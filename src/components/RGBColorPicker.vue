<template>
  <div>
    <h3>RGBColorPicker</h3>
    <div
      class="color"
      :style="{ backgroundColor: `rgb(${rValue}, ${gValue}, ${bValue})` }"
    ></div>
    <!-- $event es el dato que el componente hijo envía al padre cuando ocurre el evento. -->
    <SingleColorPicker color="r" :value="rValue" @change="updateColor('r', $event)" />
    <SingleColorPicker color="g" :value="gValue" @change="updateColor('g', $event)" />
    <SingleColorPicker color="b" :value="bValue" @change="updateColor('b', $event)" />
  </div>
</template>

<script setup>
import SingleColorPicker from './SingleColorPicker.vue';
import { ref } from 'vue';
const rValue = ref(0)
const gValue = ref(0)
const bValue = ref(0)
const updateColor = (color, value) => {
    if (color == 'r') rValue.value = value;
    else if (color == 'g') gValue.value = value;
    else if (color == 'b') bValue.value = value;
}


</script>

<style scoped>
.color {
    width: 200px;
    height: 200px;
    border: 2px solid black;
}
</style>
