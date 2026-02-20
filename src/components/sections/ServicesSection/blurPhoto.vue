<template>
    <transition>
        <div v-if="isClickOnDolls" class="absolute -inset-[0.5%] ">
            <svg @click="$emit('isClickOnBlur')" width="100%" height="100%" viewBox="0 0 311 172" fill="none" xmlns="http://www.w3.org/2000/svg">
              <foreignObject x="-11" y="-11" width="333" height="194"><div xmlns="http://www.w3.org/1999/xhtml" style="backdrop-filter:blur(5.5px);clip-path:url(#bgblur_0_1361_57_clip_path);height:100%;width:100%"></div></foreignObject><path data-figma-bg-blur-radius="11" d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z" fill="#FFD4DF" fill-opacity="0.69"/>
              <defs>
              <clipPath id="bgblur_0_1361_57_clip_path" transform="translate(11 11)"><path d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z"/>
              </clipPath></defs>
            </svg>

            <div class="absolute p-4 w-max h-[85%] m-auto inset-0 text-center text-dablue text-[17px] font-semibold flex flex-col justify-between">
              <div>{{ menuText1 }}</div>
              <div>{{ menuText2 }}</div>
              <div v-if="menuText3">{{ menuText3 }}</div>
            </div>
        </div>
    </transition>

</template>

<script setup>
import { inject, toRefs } from 'vue';

const props = defineProps(['isClickOnDolls'])
const {isClickOnDolls} = toRefs(props)

const servicesArr
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
