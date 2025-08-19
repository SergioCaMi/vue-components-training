<script setup>
import { computed } from 'vue';

const props = defineProps({
    rate: Number
})

const fillStarts = computed(() => {
    return Math.round(props.rate)
})

const emptyStarts = computed(() => {
    return 5 - fillStarts.value
})

</script>

<template>
    <div>
        <span class="filled" v-for="r in fillStarts">★</span>
        <span class="empty"  v-for="r in emptyStarts">☆</span>
    </div>
</template>

<style scoped>
span {
    font-size: 1.2rem;
}

.filled {
    color: gold;
}

.empty {
    color: #ccc;
}
</style>