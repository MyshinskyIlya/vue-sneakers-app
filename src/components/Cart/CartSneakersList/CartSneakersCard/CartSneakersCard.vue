<script setup>
const { imageUrl, title, price, deleteCartItem, id, count } = defineProps({
    item: Object,
    imageUrl: String,
    title: String,
    price: Number,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickFavorite: Function,
    deleteCartItem: Function,
    count: Number
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
            <b class="whitespace-nowrap font-bold">{{ price * count + ' RUB' }}</b>
        </div>
        <div
            class="absolute bottom-4 right-4 flex items-center gap-1 font-bold text-lime-500"
        >
            <div class="text-sm">
                {{ item.count }}
            </div>
            <img
                src="/close.svg"
                alt="Cros Icon"
                class="opacity-60 hover:opacity-100 cursor-pointer"
                @click="
                    () => {
                        deleteCartItem(item)
                    }
                "
            />
        </div>
    </div>
</template>
