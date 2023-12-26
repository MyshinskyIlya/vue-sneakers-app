<script setup>
import { onMounted, ref, watch } from 'vue'

const { setCartHandler, totalPrice, setFavHandler, cartItems, itemsCount } = defineProps({
    setCartHandler: Function,
    totalPrice: Number,
    setFavHandler: Function,
    cartItems: Array,
    itemsCount: Number
})
</script>

<template>
    <nav class="hidden lg:block cursor-pointer">
        <ul class="flex gap-6 text-6 text-sm font-light">
            <li @click="setCartHandler" class="flex items-center gap-2 hover:text-black">
                <img src="/cart.svg" alt="Cart Icon" />
                <span
                    :class="
                        totalPrice > 0
                            ? 'font-semibold whitespace-nowrap text-lime-500'
                            : 'whitespace-nowrap'
                    "
                    >{{ totalPrice > 0 ? totalPrice + ' RUB' : 'Корзина' }}</span
                >
            </li>
            <li class="flex items-center gap-2 hover:text-black" @click="setFavHandler">
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
            <li class="flex items-center gap-1" @click="setCartHandler">
                <img src="/cart.svg" alt="Cart Icon" />
                <span class="font-bold text-lime-500 text-sm">
                    {{ itemsCount > 0 ? itemsCount : '' }}
                </span>
            </li>
            <li class="flex items-center gap-2" @click="setFavHandler">
                <img src="/heart.svg" alt="Heart Icon" />
            </li>
            <li class="flex items-center gap-2">
                <img src="/profile.svg" alt="Profile Icon" />
            </li>
        </ul>
    </nav>
</template>
