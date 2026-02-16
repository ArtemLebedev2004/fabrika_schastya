<template>
    <div v-if="!isOpenYetCharacters" @click="openGallery" class="
        p-1.25
        -bottom-8
        border-[#C9185C] border
        rounded-[20px]
        "
        :class="style"
    >
        <div class="
            bg-[#E05C92] hover:bg-[#4F7A23]/0
            text-[14px] text-center text-white
            rounded-2xl md:rounded-4xl
            transition-all duration-200
            cursor-pointer
            px-5.25 md:px-5 md:py-2
        "
        :class="style2"
        >
            ПОСМОТРЕТЬ ЕЩЁ
        </div>
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps(['style', 'style2'])

const {style, style2} = toRefs(props)
</script>