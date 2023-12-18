<script setup>
const { isInputInFocus, setFocus } = defineProps({
    isInputInFocus: Boolean,
    setFocus: Function
})
</script>

<template>
    <div class="relative mt-4 md:mt-0">
        <input
            type="text"
            placeholder="Поиск..."
            class="p-2 px-11 border border-slate-200 mt-1 rounded-xl w-full md:w-80 focus:shadow-md items-center"
            @focusin="setFocus"
            @focusout="setFocus"
        />
        <img
            src="/search.svg"
            alt="Close Icon"
            class="absolute top-[16px] left-4 z-20 w-4"
        />
        <img
            v-if="isInputInFocus"
            src="/close.svg"
            alt="Close Icon"
            class="hidden md:block absolute top-[13px] right-4 z-20 w-6 cursor-pointer"
        />
    </div>
</template>
