<script setup>
import CartSneakersCard from './CartSneakersCard/CartSneakersCard.vue'
</script>

<template>
    <div class="p-10 flex flex-col gap-6 flex-1 w-full">
        <CartSneakersCard
            imageURL="/sneakers//sneakers-2.jpg"
            price="450 RUB"
            title="Чоткие кеды"
        />
        <CartSneakersCard
            imageURL="/sneakers//sneakers-3.jpg"
            price="450 RUB"
            title="Чоткие кеды"
        />
        <CartSneakersCard
            imageURL="/sneakers//sneakers-4.jpg"
            price="450 RUB"
            title="Z"
        />
        <CartSneakersCard
            imageURL="/sneakers//sneakers-1.jpg"
            price="450 RUB"
            title="Чоткие кеды Nike Blaster 3D ultra Z"
        />
    </div>
</template>
