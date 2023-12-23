<script setup>
const { setFavHandler } = defineProps({
    setFavHandler: Function
})

const isIcon = 'https://em-content.zobj.net/source/apple/354/melting-face_1fae0.png'
</script>

<template>
    <div
        class="flex flex-col gap-4 font-medium border-slate-200 p-10 justify-center items-center md:my-auto my-20"
    >
        <img
            :src="
                isIcon
                    ? 'https://em-content.zobj.net/source/apple/354/melting-face_1fae0.png'
                    : '/public/sadSmile.png'
            "
            alt="Empty Fav Icon"
            width="86"
        />
        <h2 class="text-2xl font-bold">Закладок нет :</h2>
        <p class="text-6 text-center font-light">Вы ничего не добавляли в закладки</p>
        <button
            class="bg-lime-400 hover:bg-lime-500 active:bg-lime-600 disabled:bg-slate-300 disabled:cursor-auto transition-all duration-400 rounded-2xl px-4 py-3 font-bold text-white cursor-pointer mt-12"
            @click="setFavHandler"
        >
            Вернуться назад
        </button>
    </div>
</template>
