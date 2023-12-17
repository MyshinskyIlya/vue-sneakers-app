<script setup>
import Header from './components/Header/Header.vue'
import Wrapper from './components/Wrapper.vue'
import SneakersList from './components/SneakersList/SneakersList.vue'
import Cart from './components/Cart/Cart.vue'
</script>

<template>
    <Wrapper>
        <Header />
        <SneakersList />
    </Wrapper>
    <Cart />
</template>
