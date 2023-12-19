<script setup>
import { watch } from 'vue'

const { isInputInFocus, setFocus, searchQuery } = defineProps({
    isInputInFocus: Boolean,
    setFocus: Function,
    onChangeInput: Function
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
            @input="(e) => onChangeInput(e.target.value)"
        />
        <img
            src="/search.svg"
            alt="Close Icon"
            class="absolute top-[16px] left-4 z-20 w-4"
        />
    </div>
</template>
