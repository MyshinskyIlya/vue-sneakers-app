<script setup>
import Logo from './Logo/Logo.vue'
import Links from './Links/Links.vue'

const { setCartHandler, totalPrice, setFavHandler, cartItems, itemsCount } = defineProps({
    setCartHandler: Function,
    totalPrice: Number,
    setFavHandler: Function,
    cartItems: Array,
    itemsCount: Number
})
</script>

<template>
    <header
        class="flex justify-between items-center h-[41px] px-8 py-10 border-b border-slate-100"
    >
        <Logo />
        <Links
            :setCartHandler="setCartHandler"
            :totalPrice="totalPrice"
            :setFavHandler="setFavHandler"
            :cartItems="cartItems"
            :itemsCount="itemsCount"
        />
    </header>
</template>

<style></style>
