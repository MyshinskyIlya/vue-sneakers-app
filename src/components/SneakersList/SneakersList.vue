<script setup>
import SneakersCard from './SneakersCard/SneakersCard.vue'

const { items } = defineProps({
    items: Array
})
</script>

<template>
    <section class="md:mt-8">
        <div class="grid md:grid-cols-3 lg:grid-cols-4 gap-6 mt-6 space-y-4 md:space-y-0">
            <SneakersCard
                v-for="item in items"
                :key="item.id"
                :imageUrl="item.imageUrl"
                :title="item.title"
                :price="item.price"
                :isAdded="false"
                :isFavorite="item.isFavorite"
                :item="item"
            />
        </div>
    </section>
</template>
