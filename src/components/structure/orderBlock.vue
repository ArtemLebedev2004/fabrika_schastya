<template>
  <div @click="isOpenOrder = !isOpenOrder" class="border-dablue border rounded-[29px] p-[2%]">
    <div class="flex flex-col gap-[13px] bg-daliblue rounded-[24px] px-[5%] py-[4%] ">
      <div class=" text-center text-white">
        ЗАКАЗАТЬ <br> ИЛИ УЗНАТЬ ПОДРОБНЕЕ
      </div>
    </div>
  </div>

  <transition>
    <div v-if="isOpenOrder" class="flex flex-col gap-[23px]">
      <div>
        <div class="flex justify-center gap-7">
          <div class="relative basis-1/6">
            <img src="/src/assets/icons/vk_color.svg" alt="" class="w-full">
            <div class="absolute top-[40%] -left-[20%] -right-[5%] bottom-0 border-dablue border rounded-[39px] -z-1"></div>
          </div>

          <div class="relative basis-1/6">
            <img src="/src/assets/icons/wa_color.svg" alt="" class="w-full">
            <div class="absolute top-[40%] -left-[20%] -right-[5%] bottom-0 border-green-400 border rounded-[39px] -z-1"></div>
          </div>

          <div class="relative basis-1/6">
            <img src="/src/assets/icons/tg_color.svg" alt="" class="w-full">
            <div class="absolute top-[40%] -left-[20%] -right-[5%] bottom-0 border-liliblue border rounded-[39px] -z-1"></div>
          </div>

          <div class="relative basis-1/6">
            <img src="/src/assets/icons/max_color.svg" alt="" class="w-full">
            <div class="absolute top-[40%] -left-[20%] -right-[5%] bottom-0 border-purple-600 border rounded-[39px] -z-1"></div>
          </div>
        </div>
      </div>

      <a href="tel: +79171772625" class="border-dablue border text-[17px] flex items-center justify-center gap-2 px-[5%] py-[3%] rounded-full">
        <div class="w-[8%]">
          <svg viewBox="0 0 26 25" fill="none" xmlns="http://www.w3.org/2000/svg" class="">
            <path d="M18.1376 16.0383L17.4803 16.7045C17.4803 16.7045 15.916 18.2869 11.6477 13.9663C7.37941 9.64564 8.94373 8.06327 8.94373 8.06327L9.35684 7.64268C10.3781 6.61032 10.4748 4.95148 9.58362 3.73971L7.76363 1.26469C6.66008 -0.235326 4.52954 -0.433857 3.26566 0.845565L0.997897 3.1397C0.372456 3.775 -0.0464299 4.59559 0.0041253 5.50737C0.134124 7.84121 1.17123 12.8604 6.95475 18.7163C13.0893 24.9252 18.8453 25.1722 21.1983 24.9487C21.9436 24.8781 22.5908 24.4928 23.1122 23.9634L25.1633 21.8869C26.5499 20.4854 26.16 18.081 24.3862 17.1001L21.6273 15.5722C20.4631 14.9295 19.0476 15.1177 18.1376 16.0383Z" fill="#397BD8"/>
          </svg>
        </div>

        <div class="text-dablue">
          +7 (917) 177-26-25
        </div>
      </a>

      <a href="mail: Fabrika_schastya_moocp@mail.ru" class="border-dablue border text-[17px] flex items-center justify-center gap-2 px-[5%] py-[3.8%] rounded-full">
        <div class="text-dablue text-[14px]">
          Fabrika_schastya_moocp@mail.ru
        </div>
      </a>
    </div>
  </transition>
  
  
</template>

<script setup>
import { ref } from 'vue';

let isOpenOrder = ref(false)
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