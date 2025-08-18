<template>
<div>
    <p>Random value between {{ min }} and {{ max }} => {{ random }}</p>
</div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    min: Number,
    max: Number
});

const random = computed(() => {
    return Math.floor(Math.random() * (props.max - props.min + 1)) + props.min;
});


</script>

<style scoped>
</style>
