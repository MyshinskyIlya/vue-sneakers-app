<script setup>
const { imageURL, title, price } = defineProps({
    imageURL: String,
    title: String,
    price: String,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickAdd: Function,
    onClickFavorite: Function
})
</script>

<template>
    <div
        class="relative shadow-md rounded-2xl py-6 px-6 flex flex-col justify-center items-center border bg-white border-slate-200 hover:shadow-xl hover:scale-105 transition-all ease-in-out"
    >
        <div class="w-full flex flex-1 justify-center items-center">
            <img
                :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
                alt="Like Icon"
                width="42"
                height="42"
                class="absolute top-6 left-4 cursor-pointer"
                @click="onClickFavorite"
            />
            <img :src="imageURL" alt="Sneaker Image" class="object-contain" />
        </div>
        <p class="capitalize trxt-md font-semibold text-lg w-full mt-2">{{ title }}</p>
        <div class="flex items-center justify-between w-full mt-2">
            <div>
                <p class="text-slate-300">ЦЕНА:</p>
                <b class="whitespace-nowrap font-bold">{{ price }}</b>
            </div>
            <div>
                <img
                    @click="onClickAdd"
                    :src="!isAdded ? '/plus.svg' : '/checked.svg'"
                    alt="Plus Icon"
                    class="cursor-pointer"
                />
            </div>
        </div>
    </div>
</template>
