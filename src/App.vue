<script setup>
import IdCard from "./components/IdCard.vue";
import Random from "./components/Random.vue";
import BoxColor from "./components/BoxColor.vue";
</script>

<template>
  <h1>Creación de componentes con Vue</h1>
  <p>Crea a conitnuación todos los componentes del ejercicio.</p>

  <h2>Iteration 1 | Component: IdCard</h2>
  <IdCard last-name="Doe" first-name="John" gender="male" :height="178" :birth="new Date('1992-07-14')" picture="https://randomuser.me/api/portraits/men/44.jpg" />
  <IdCard last-name="Delores " first-name="Obrien" gender="female" :height="172" :birth="new Date('1988-05-11')" picture="https://randomuser.me/api/portraits/women/44.jpg" />

  <h2>Iteration 2 | Component: Random</h2>
  <Random :min="1" :max="6" />
  <Random :min="1" :max="100" />

  <h2>Iteration 3 | Component: BoxColor</h2>
  <BoxColor :r="255" :g="0" :b="0" />
  <BoxColor :r="128" :g="255" :b="0" />
</template>

<style scoped>
h2 {
  margin: 3rem 0;
}
</style>
