<template>
  <div class="card" :style="{ backgroundColor: `${bgColor}`, color:`${color}`}">
    <img :src="tipo" alt="" />
    <p class="number">{{ ocultar(props.number) }}</p>
    <div class="data">
        <p>Expires {{ expirationMonth }}/{{ expirationYear }}  {{ bank }}</p>
        <p>{{ owner }}</p>
    </div>

  </div>
</template>

<script setup>
import { computed } from 'vue';
import visaImg from '../assets/images/visa.png'
import masterImg from '../assets/images/master-card.svg'

const tipo = computed(()=>{
    return props.type == 'Visa' ? visaImg : masterImg 
})

function ocultar(str) {
    str = String(str);
    const ultimos = str.slice(-4);
    const ocultos = '*'.repeat(str.length - 4);
    const resultado = ocultos + ultimos;
    return resultado.replace(/(.{4})/g, '$1 ').trim();
}

const props = defineProps({
  type: {
    type: String,
    validator: (value) => ["Visa", "Master Card"].includes(value),
  },
  number: Number,
  expirationMonth: {
    type: Number,
    validator: (num) => num >= 0 && num <= 12,
  },
  expirationYear: Number,
  bank: String,
  owner: String,
  bgColor: String,
  color: String,
});
</script>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  margin: 2rem;
  width: 300px;
  height: 180px;
  border: 1px solid #ccc;
  border-radius: 10px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  padding: 15px;
  position: relative;
  font-family: 'Arial', sans-serif;
}

.card img {
  width: 50px;
  object-fit: contain;
  position: absolute;
  top: 15px;
  right: 15px;
}

.card .number {
  font-size: 25px;
  margin: 40px 20px;
  text-align: center;
}

.data {
  font-size: 14px;
}

</style>
