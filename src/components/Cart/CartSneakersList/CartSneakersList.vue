<script setup>
import CartSneakersCard from './CartSneakersCard/CartSneakersCard.vue'

const { cardItems } = defineProps({
    cardItems: Array
})
</script>

<template>
    <div class="p-10 flex flex-col gap-6 flex-1 w-full">
        <CartSneakersCard
            v-for="item in cardItems"
            :imageUrl="item.imageUrl"
            :price="item.price + ' RUB'"
            :title="item.title"
        />
    </div>
</template>
