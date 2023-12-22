<script setup>
import Logo from './Logo/Logo.vue'
import Links from './Links/Links.vue'
import HeaderImage from './HeaderImage/HeaderImage.vue'

const { setCartHandler, totalPrice, setFavHandler } = defineProps({
    setCartHandler: Function,
    totalPrice: Number,
    setFavHandler: Function
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
        />
    </header>
</template>

<style></style>
