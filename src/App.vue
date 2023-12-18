<script setup>
import Header from './components/Header/Header.vue'
import Wrapper from './components/Wrapper.vue'
import SneakersList from './components/SneakersList/SneakersList.vue'
import Cart from './components/Cart/Cart.vue'
import SearchBar from './components/SearchBar/SearchBar.vue'
import { ref } from 'vue'

const isCartOpen = ref(false)
const isInputInFocus = ref(false)

const setCartHandler = () => {
    isCartOpen.value = !isCartOpen.value
}

const setFocus = () => {
    isInputInFocus.value = !isInputInFocus.value
}

console.log(isInputInFocus.value)
</script>
<template>
    <Wrapper>
        <Header :setCartHandler="setCartHandler" />
        <div
            class="md:mt-12 flex md:flex-row flex-col md:justify-between md:items-center"
        >
            <h2 class="text-4xl font-bold mt-4 md:mt-0">Все Кросcовки</h2>
            <SearchBar :isInputInFocus="isInputInFocus" :setFocus="setFocus" />
        </div>
        <SneakersList />
    </Wrapper>
    <Cart v-if="isCartOpen" :setCartHandler="setCartHandler" />
</template>
