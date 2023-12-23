<script setup>
import { inject, ref } from 'vue'

const { imageUrl, title, price, isFavorite, item } = defineProps({
    imageUrl: String,
    title: String,
    price: Number,
    isFavorite: Boolean,
    isAdded: Boolean,
    onClickFavorite: Function,
    item: Object
})

const addToFavorite = inject('addToFavorite')
const addtoCart = inject('addtoCart')

const timer = ref(false)
function addTimer() {
    timer.value = true

    setTimeout(() => {
        timer.value = false
    }, 300)
}
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
                @click="() => addToFavorite(item)"
            />
            <img :src="imageUrl" alt="Sneaker Image" class="object-contain" />
        </div>
        <p class="capitalize trxt-md font-semibold text-lg w-full mt-2">{{ title }}</p>
        <div class="flex items-center justify-between w-full mt-2 gap-2">
            <div>
                <p class="text-slate-300">ЦЕНА:</p>
                <b class="whitespace-nowrap font-bold">{{ price + ' RUB' }}</b>
            </div>
            <div class="flex items-center gap-1 self-end mt-5">
                <span class="font-bold text-sm text-lime-500">
                    {{ item.count > 0 ? item.count : '' }}
                </span>
                <img
                    @click="
                        () => {
                            addtoCart(item)
                            addTimer()
                        }
                    "
                    :src="!timer ? '/plus.svg' : '/checked.svg'"
                    alt="Plus Icon"
                    :class="
                        !timer
                            ? 'cursor-pointer '
                            : 'scale-150 rotate-6 duration-200 transition-all ease-in-out'
                    "
                />
            </div>
        </div>
    </div>
</template>
