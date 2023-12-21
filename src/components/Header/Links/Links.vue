<script setup>
const { setCartHandler, totalPrice } = defineProps({
    setCartHandler: Function,
    totalPrice: Number
})
</script>

<template>
    <nav class="hidden lg:block cursor-pointer">
        <ul class="flex gap-6 text-6 text-sm font-light">
            <li @click="setCartHandler" class="flex items-center gap-2 hover:text-black">
                <img src="/cart.svg" alt="" />
                <span
                    :class="
                        totalPrice > 0
                            ? 'font-semibold whitespace-nowrap text-lime-500'
                            : 'whitespace-nowrap'
                    "
                    >{{ totalPrice > 0 ? totalPrice + ' RUB' : 'Корзина' }}</span
                >
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
            <li class="flex items-center gap-2" @click="setCartHandler">
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
