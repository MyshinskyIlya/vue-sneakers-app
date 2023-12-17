<script setup>
const { setCartHandler } = defineProps({
    setCartHandler: Function
})
</script>

<template>
    <nav class="hidden lg:block cursor-pointer">
        <ul class="flex gap-6 text-6 text-sm font-light">
            <li @click="setCartHandler" class="flex items-center gap-2 hover:text-black">
                <img src="/cart.svg" alt="" />
                <span class="font-semibold whitespace-nowrap">12205 руб.</span>
            </li>
            <li class="flex items-center gap-2 hover:text-black">
                <img src="/heart.svg" alt="" />
                <span>Закладки</span>
            </li>
            <li class="flex items-center gap-2 hover:text-black">
                <img src="/profile.svg" alt="" />
                <span>Профиль</span>
            </li>
        </ul>
    </nav>
    <nav class="lg:hidden cursor-pointer">
        <ul class="flex gap-6 text-6 text-sm font-light">
            <li class="flex items-center gap-2">
                <img src="/cart.svg" alt="" />
            </li>
            <li class="flex items-center gap-2">
                <img src="/heart.svg" alt="" />
            </li>
            <li class="flex items-center gap-2">
                <img src="/profile.svg" alt="" />
            </li>
        </ul>
    </nav>
</template>
