<template>
    <div>
        <img @click="diceRoll" :src="dice" alt="">
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import dice1 from '../assets/images/dice1.png'
import dice2 from '../assets/images/dice2.png'
import dice3 from '../assets/images/dice3.png'
import dice4 from '../assets/images/dice4.png'
import dice5 from '../assets/images/dice5.png'
import dice6 from '../assets/images/dice6.png'
import diceEmpty from '../assets/images/dice-empty.png'

const diceImages = [dice1, dice2, dice3, dice4, dice5, dice6]
const dice = ref(null)
const diceRoll = () => {
    dice.value = diceEmpty
    //TODO: Limpiar el setTimeout para que se quede sólo con la última tirada
    setTimeout(() => {
        const randomIndex = Math.floor(Math.random() * diceImages.length)
        dice.value = diceImages[randomIndex]
    }, 1000)
}
onMounted(() => {
  diceRoll()
})
</script>

<style scoped>
img {
    width: 200px;
    height: 200px;
    background-color: #ccc;
    border-radius: 30px;
}
</style>