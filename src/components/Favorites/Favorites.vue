<script setup>
import SneakersList from '../SneakersList/SneakersList.vue'
import FavoritesEmpty from './FavoritesEmpty/FavoritesEmpty.vue'

const { favItems, addtoCart, addToFavorite } = defineProps({
    favItems: Array,
    addtoCart: Function,
    setFavHandler: Function,
    addToFavorite: Function
})
</script>

<template>
    <div class="w-full h-screen bg-white overflow-y-auto flex flex-col z-10">
        <div class="flex items-center ml-10 cursor-pointer" @click="setFavHandler">
            <svg
                width="12"
                height="20"
                viewBox="0 0 7 12"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
                class="rotate-180 hover:rotate-0 transition-all ease-in-out duration-500"
            >
                <path
                    d="M1 0.999999L6 6L1 11"
                    stroke="#C8C8C8"
                    stroke-width="1.5"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                />
            </svg>

            <h2 class="text-2xl font-bold p-8">Закладки</h2>
        </div>
        <FavoritesEmpty v-if="favItems.length < 1" />
        <SneakersList
            v-if="favItems"
            :items="favItems"
            :addtoCart="addtoCart"
            :addToFavorite="addToFavorite"
        />
    </div>
</template>
