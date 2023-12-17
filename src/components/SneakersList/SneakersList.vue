<script setup>
import SneakersCard from './SneakersCard/SneakersCard.vue'

const images = [
    '/sneakers//sneakers-1.jpg',
    '/sneakers//sneakers-2.jpg',
    '/sneakers//sneakers-3.jpg',
    '/sneakers//sneakers-4.jpg',
    '/sneakers//sneakers-6.jpg',
    '/sneakers//sneakers-7.jpg',
    '/sneakers//sneakers-8.jpg',
    '/sneakers//sneakers-9.jpg',
    '/sneakers//sneakers-10.jpg',
    '/sneakers//sneakers-11.jpg',
    '/sneakers//sneakers-12.jpg'
]

const onClickAdd = () => {
    alert(1)
}
</script>

<template>
    <section class="mt-2 md:mt-10 py-4">
        <h2 class="text-4xl font-bold">Все Кросcовки</h2>
        <div class="grid md:grid-cols-3 lg:grid-cols-4 gap-6 mt-6 space-y-4 md:space-y-0">
            <SneakersCard
                :imageURL="images[0]"
                title="Ровные педали"
                price="12500 RUB"
                isAdded
                isFavorite
                :onClickAdd="onClickAdd"
            />
            <SneakersCard :imageURL="images[1]" />
            <SneakersCard :imageURL="images[2]" />
            <SneakersCard :imageURL="images[3]" />
            <SneakersCard :imageURL="images[4]" />
            <SneakersCard :imageURL="images[5]" />
            <SneakersCard :imageURL="images[6]" />
            <SneakersCard :imageURL="images[7]" />
            <SneakersCard :imageURL="images[8]" />
            <SneakersCard :imageURL="images[9]" />
            <SneakersCard :imageURL="images[10]" />
        </div>
    </section>
</template>
