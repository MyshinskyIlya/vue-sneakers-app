<script setup>
import { onMounted, watch, ref, provide } from 'vue'
import axios from 'axios'
import Header from './components/Header/Header.vue'
import Wrapper from './components/Wrapper.vue'
import SneakersList from './components/SneakersList/SneakersList.vue'
import Cart from './components/Cart/Cart.vue'
import Favorites from './components/Favorites/Favorites.vue'
import SearchBar from './components/SearchBar/SearchBar.vue'
import Sneakers from './assets/Sneakers'
import HeaderImage from './components/Header/HeaderImage/HeaderImage.vue'

const totalPrice = ref(0)
const searchQuery = ref('')
const items = ref([])
const cartItems = ref([])
const favItems = ref([])

const isCartOpen = ref(false)
const isFavOpen = ref(false)

onMounted(async () => {
    try {
        const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items')
        items.value = data

        items.value = items.value.map((obj) => ({
            ...obj,
            isFavorite: false,
            isAdded: false,
            count: 0
        }))
    } catch (error) {
        console.log('API loading Error: Downloading from the local state')
        items.value = Sneakers
    }

    items.value[0].isFavourite = true
})

watch(searchQuery, async () => {
    try {
        const { data } = await axios.get(
            'https://604781a0efa572c1.mokky.dev/items?title=*' + searchQuery.value
        )
        items.value = data
    } catch (error) {
        console.log('API loading Error: Filter by Search from the local state')
        items.value = Sneakers.filter((i) =>
            i.title.toLowerCase().includes(searchQuery.value.toLowerCase())
        )
    }
})

const onChangeInput = (e) => {
    searchQuery.value = e
}

const setCartHandler = () => {
    isCartOpen.value = !isCartOpen.value
}

const setFavHandler = () => {
    isFavOpen.value = !isFavOpen.value
}

const addToFavorite = async (item) => {
    item.isFavorite = !item.isFavorite

    if (favItems.value.includes(item)) {
        favItems.value = favItems.value.filter((i) => i.id != item.id)
    }
    if (!favItems.value.includes(item) && item.isFavorite) {
        favItems.value.push(item)
    }
}

const addtoCart = async (item) => {
    item.isAdded = !item.isAdded
    item.count++
    totalPrice.value += item.price

    if (!cartItems.value.includes(item)) {
        cartItems.value.push(item)
    }
}

const deleteCartItem = async (item) => {
    if (item.count == 1) {
        cartItems.value = cartItems.value.filter((i) => i.id != item.id)
    }
    item.count--

    totalPrice.value -= item.price
}

provide('addToFavorite', addToFavorite)
provide('addtoCart', addtoCart)
</script>

<template>
    <Wrapper>
        <Header
            :setCartHandler="setCartHandler"
            :setFavHandler="setFavHandler"
            :totalPrice="totalPrice"
            :cartItems="cartItems"
        />
        <div v-if="!isFavOpen">
            <HeaderImage />
            <div
                class="md:mt-12 flex md:flex-row flex-col md:justify-between md:items-center"
            >
                <h2 class="text-4xl font-bold mt-4 md:mt-0">Все Кросcовки</h2>
                <SearchBar :onChangeInput="onChangeInput" />
            </div>

            <SneakersList :items="items" />
        </div>
        <Favorites
            v-if="isFavOpen"
            :favItems="favItems"
            :addtoCart="addtoCart"
            :setFavHandler="setFavHandler"
            :addToFavorite="addToFavorite"
        ></Favorites>
    </Wrapper>
    <Cart
        v-if="isCartOpen"
        :setCartHandler="setCartHandler"
        :cartItems="cartItems"
        :totalPrice="totalPrice"
        :deleteCartItem="deleteCartItem"
    />
</template>
