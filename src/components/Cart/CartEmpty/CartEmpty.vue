<script setup>
const { setCartHandler } = defineProps({
    setCartHandler: Function
})
</script>

<template>
    <div
        class="flex flex-col gap-4 font-medium border-slate-200 p-10 justify-center items-center my-auto"
    >
        <img src="/public/package-icon.png" alt="Empty Cart Icon" width="260" />
        <h2 class="text-2xl font-bold">Корзина пустая</h2>
        <p class="text-6 text-center font-light">
            Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ.
        </p>
        <button
            class="bg-lime-400 hover:bg-lime-500 active:bg-lime-600 disabled:bg-slate-300 disabled:cursor-auto transition-all duration-400 rounded-2xl px-4 py-3 font-bold text-white cursor-pointer w-full mt-auto"
            @click="setCartHandler"
        >
            Вернуться назад
        </button>
    </div>
</template>
