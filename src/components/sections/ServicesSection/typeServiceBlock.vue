<template>
    <div @click="swimBlur()">
        <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
                :fill="isOpenDolls ? '#397BD8' : '#C9185C'"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
                <img :src="serv_type_photo" alt="" class="w-full h-full rounded-4xl min-[415px]:rounded-[36px]">
                <blurPhoto
                  :isClickOnDolls="isClickOnDolls"
                  @isClickOnBlur="isClickOnBlur = true"
                />
            </div>

            <div @click="isClickOnArrow = true" class="absolute right-0 left-[83.7%] -top-[7.8%]">
                <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                :stroke="isOpenDolls ? '#397BD8' : '#C9185C'"/>
                </svg>

                <div class="absolute inset-[15%] rounded-full flex items-center p-[16%]" :class="isOpenDolls ? 'bg-liblue' : 'bg-lipink'">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block w-full transition-all duration-150" :class="isOpenDolls ? ' rotate-180' : ''">
                </div>
            </div>
        </div>

        <div class="text-[20px] font-semibold mt-2">
        {{title_type}}
        </div>
    </div>
</template>

<script setup>
import { ref, toRefs } from 'vue';

import blurPhoto from './blurPhoto.vue';

const props = defineProps(['serv_type_photo', 'title_type'])
const {serv_type_photo, title_type} = toRefs(props)

let isClickOnDolls = ref(false)
let isClickOnBlur = ref(false)
let isClickOnArrow = ref(false)

function swimBlur() {
  if (!isClickOnBlur.value) {
    if (isClickOnArrow.value && isClickOnDolls.value) {
      isClickOnDolls.value = false
    } else {
      isClickOnDolls.value = true
    }
  } else {
    isClickOnDolls.value = false
  }
  isClickOnArrow.value = false
  isClickOnBlur.value = false

}
</script>
