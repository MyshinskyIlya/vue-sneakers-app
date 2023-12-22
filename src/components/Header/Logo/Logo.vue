<script setup>
const reloadPage = () => {
    document.location.reload()
}
</script>

<template>
    <div class="flex gap-4 items-center cursor-pointer" @click="reloadPage">
        <img src="/logo.png" alt="Logo" width="40" height="40" class="object-contain" />
        <div class="flex flex-col">
            <h2 class="text-lg font-extrabold -mb-1">VUE SNEAKERS</h2>

            <p class="hidden lg:block text-md text-6 font-light">
                Магазин лучших кроссовок
            </p>
        </div>
    </div>
</template>
