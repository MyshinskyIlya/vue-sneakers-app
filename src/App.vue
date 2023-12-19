<script setup>
import { onMounted, watch, ref } from 'vue'
import axios from 'axios'
import Header from './components/Header/Header.vue'
import Wrapper from './components/Wrapper.vue'
import SneakersList from './components/SneakersList/SneakersList.vue'
import Cart from './components/Cart/Cart.vue'
import SearchBar from './components/SearchBar/SearchBar.vue'
import Sneakers from './assets/Sneakers'

const items = ref([])

const searchQuery = ref('')

const onChangeInput = (e) => {
    searchQuery.value = e
}

onMounted(async () => {
    try {
        const { data } = await axios.get('https://604781a0efa572c1.mokky.dev/items')
        items.value = data
    } catch (error) {
        console.log('API loading Error: Downloading from the local state')
        items.value = Sneakers
    }
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

const isCartOpen = ref(false)
const isInputInFocus = ref(false)

const setCartHandler = () => {
    isCartOpen.value = !isCartOpen.value
}

const setFocus = () => {
    isInputInFocus.value = !isInputInFocus.value
}
</script>
<template>
    <Wrapper>
        <Header :setCartHandler="setCartHandler" />
        <div
            class="md:mt-12 flex md:flex-row flex-col md:justify-between md:items-center"
        >
            <h2 class="text-4xl font-bold mt-4 md:mt-0">Все Кросcовки</h2>
            <SearchBar
                :isInputInFocus="isInputInFocus"
                :setFocus="setFocus"
                :onChangeInput="onChangeInput"
            />
        </div>
        <SneakersList :items="items" />
    </Wrapper>
    <Cart v-if="isCartOpen" :setCartHandler="setCartHandler" />
</template>
