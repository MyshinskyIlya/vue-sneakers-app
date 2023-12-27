<script setup>
import CartSneakersCard from './CartSneakersCard/CartSneakersCard.vue'

const { cardItems, deleteCartItem } = defineProps({
    cartItems: Array,
    deleteCartItem: Function
})
</script>

<template>
    <div class="p-10 flex flex-col gap-6 flex-1 w-full" v-auto-animate>
        <CartSneakersCard
            v-for="item in cartItems"
            :item="item"
            :count="item.count"
            :imageUrl="item.imageUrl"
            :price="item.price"
            :title="item.title"
            :deleteCartItem="deleteCartItem"
        />
    </div>
</template>
