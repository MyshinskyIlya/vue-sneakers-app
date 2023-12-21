<script setup>
import { onMounted } from 'vue'

const { imageUrl, title, price } = defineProps({
    imageUrl: String,
    title: String,
    price: String,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickFavorite: Function
})
</script>

<template>
    <div
        class="relative grid grid-cols-3 gap-6 items-center shadow-md rounded-2xl py-6 px-6 border bg-white border-slate-200 hover:shadow-xl hover:scale-105 transition-all ease-in-out cursor-pointer"
    >
        <div class="flex justify-end items-center col-span-1">
            <img :src="imageUrl" alt="Sneaker Image" class="object-contain" width="96" />
        </div>
        <div class="col-span-2">
            <p class="capitalize text-lg w-full">{{ title }}</p>
            <b class="whitespace-nowrap font-bold">{{ price }}</b>
        </div>
        <img
            src="/close.svg"
            alt="Cros Icon"
            class="absolute bottom-4 right-4 opacity-60 hover:opacity-100 cursor-pointer"
        />
    </div>
</template>
