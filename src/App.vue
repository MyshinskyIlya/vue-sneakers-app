<script setup>
import Header from './components/Header/Header.vue'
import Wrapper from './components/Wrapper.vue'
import SneakersList from './components/SneakersList/SneakersList.vue'
import Cart from './components/Cart/Cart.vue'
import { ref } from 'vue'

const isCartOpen = ref(false)

const setCartHandler = () => {
    isCartOpen.value = !isCartOpen.value
}
</script>
<template>
    <Wrapper>
        <Header :setCartHandler="setCartHandler" />
        <SneakersList />
    </Wrapper>
    <Cart v-if="isCartOpen" :setCartHandler="setCartHandler" />
</template>
