<template>
    <transition>
        <div v-if="isClickOnDolls" class="absolute -inset-x-[0.3%] -inset-y-[0.5%]">
            <svg width="100%" height="100%" viewBox="0 0 311 174" fill="none" xmlns="http://www.w3.org/2000/svg">
                <foreignObject x="-11" y="-11" width="333" height="196"><div xmlns="http://www.w3.org/1999/xhtml" style="backdrop-filter:blur(5.5px);clip-path:url(#bgblur_0_1361_57_clip_path);height:100%;width:100%"></div></foreignObject><path data-figma-bg-blur-radius="11" d="M261 0C261 19.8822 277.118 36 297 36C301.966 36 306.696 34.9941 311 33.1758V142C311 159.673 296.673 174 279 174H32C14.3269 174 0 159.673 0 142V32C0 14.3269 14.3269 0 32 0H261Z" fill="#FFD4DF" fill-opacity="0.69"/>
                <defs>
                <clipPath id="bgblur_0_1361_57_clip_path" transform="translate(11 11)"><path d="M261 0C261 19.8822 277.118 36 297 36C301.966 36 306.696 34.9941 311 33.1758V142C311 159.673 296.673 174 279 174H32C14.3269 174 0 159.673 0 142V32C0 14.3269 14.3269 0 32 0H261Z"/>
                </clipPath></defs>
            </svg>
        </div>
    </transition>
    
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps(['isClickOnDolls'])
const {isClickOnDolls} = toRefs(props)
</script>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  transform: translateX(-100vw);
}
</style>