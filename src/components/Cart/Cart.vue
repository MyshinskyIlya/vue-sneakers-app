<script setup>
import CartSneakersList from './CartSneakersList/CartSneakersList.vue'
import CartEmpty from './CartEmpty/CartEmpty.vue'
import CartSuccess from './CartSuccess/CartSuccess.vue'
import { ref } from 'vue'

const { setCartHandler, cartItems, totalPrice, deleteCartItem, isSubmit, sumbitHandler } =
    defineProps({
        setCartHandler: Function,
        cartItems: Array,
        totalPrice: Number,
        deleteCartItem: Function,
        isSubmit: Boolean,
        sumbitHandler: Function
    })
</script>

<template>
    <div
        @click="setCartHandler"
        class="fixed top-0 left-0 w-full h-screen bg-black opacity-50"
    ></div>
    <div
        class="fixed top-0 right-0 md:w-1/3 w-full h-full bg-white overflow-y-auto flex flex-col z-10"
    >
        <div
            class="flex items-center ml-10 border-b border-slate-200 cursor-pointer"
            @click="setCartHandler"
        >
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

            <h2 class="text-2xl font-bold p-8">Корзина</h2>
        </div>
        <CartEmpty
            v-if="cartItems.length == 0 && !isSubmit"
            :setCartHandler="setCartHandler"
        />
        <div v-if="cartItems.length > 0" class="flex flex-col h-full">
            <CartSneakersList
                :cartItems="cartItems"
                :deleteCartItem="deleteCartItem"
                v-if="!isSubmit"
            />
            <div
                class="flex flex-col gap-4 border-t font-medium border-slate-200 p-10"
                v-if="!isSubmit"
            >
                <div class="flex justify-between">
                    <p class="text-6">Итого:</p>
                    <p class="font-bold">{{ totalPrice }} RUB</p>
                </div>
                <div class="flex justify-between mb-1">
                    <p class="text-6">Налог 5%:</p>
                    <p class="font-bold">{{ ((totalPrice * 5) / 100).toFixed(0) }} RUB</p>
                </div>
                <button
                    @click="sumbitHandler"
                    class="bg-lime-400 hover:bg-lime-500 active:bg-lime-600 disabled:bg-slate-300 disabled:cursor-auto transition-all duration-400 rounded-2xl px-4 py-3 font-bold text-white cursor-pointer w-full mt-auto"
                >
                    Оформить Заказ
                </button>
            </div>
        </div>
        <CartSuccess v-if="isSubmit" :setCartHandler="setCartHandler" />
    </div>
</template>
