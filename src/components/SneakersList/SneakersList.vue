<script setup>
import SneakersCard from './SneakersCard/SneakersCard.vue'

const { items } = defineProps({
    items: Array
})

const onClickAdd = () => {
    alert(1)
}
</script>

<template>
    <section class="md:mt-8">
        <div class="grid md:grid-cols-3 lg:grid-cols-4 gap-6 mt-6 space-y-4 md:space-y-0">
            <SneakersCard
                v-for="item in items"
                :key="item.id"
                :imageURL="item.imageUrl"
                :title="item.title"
                :price="item.price + ' RUB'"
                :isAdded="false"
                :isFavorite="false"
                :onClickAdd="onClickAdd"
            />
        </div>
    </section>
</template>
