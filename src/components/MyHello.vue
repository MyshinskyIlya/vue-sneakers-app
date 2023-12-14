<script setup>
import { ref } from 'vue'

const count = ref(1)

function increment() {
    console.log(count)
    count.value++
}
</script>

<template>
    <h1>{{ count }}</h1>
    <p>sadasd</p>
    <button @click="increment">+</button>
    <input v-model="count" />
</template>
