<script setup>
import Logo from './Logo/Logo.vue'
import Links from './Links/Links.vue'
import HeaderImage from './HeaderImage/HeaderImage.vue'
</script>

<template>
    <header
        class="flex justify-between items-center h-[41px] px-8 py-12 border-b border-slate-100"
    >
        <Logo />
        <Links />
    </header>
    <HeaderImage />
</template>

<style></style>
