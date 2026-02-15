<template>
  <div class="relative ">
    <div class="relative max-lg:max-w-[450px] xl:w-[1280px] m-auto px-4.5 md:px-4 xl:px-10 mt-[61px] -z-10">
      <h2 class="
        font-[Soroka] text-liblue
        text-[50px] md:text-[85px] lg:text-[63px]
        leading-none
      ">
        Галерея
      </h2>

      <div class="px-8 py-[15px] border-dapink border rounded-[25px] mt-7 text-dablue text-[14px] text-center">
        Эти фотографии подобраны специально для Вас
      </div>

      <div class="relative flex mt-[30px] gap-[13px]">
        <div class="flex flex-col gap-[13px]">
          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto1.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto3.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto6.jpg" alt="" class="rounded-[18px]">
          </div>
        </div>

        <div class="flex flex-col gap-[13px]">
          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto2.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto4.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto5.jpg" alt="" class="rounded-[18px]">
          </div>
        </div>

        <div class="absolute -top-[15px] left-[40%] right-[40%]">
          <img src="/src/assets/icons/gcircle_red.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[24.2%] left-[4%] right-[78.7%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[30%] left-[40%] right-[35%]">
          <img src="/src/assets/icons/gcircle_red.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[61.4%] left-[78.7%] right-[4%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[66.5%] left-[16%] right-[64%]">
          <img src="/src/assets/icons/gcircle_red.svg" alt="" class="w-full">
        </div>

        <div v-if="!isOpenGallery" class="absolute inset-x-0 top-[72.5%] -bottom-[1%] bg-linear-to-t from-white from-14% to-white/0 to-100%">

        </div>

      </div>



      <div v-if="isOpenGallery" class="
        relative
        flex
        mt-[13px] gap-[13px]
        animate-stretch
      ">
        <div class="flex flex-col gap-[13px]">
          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto7.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto9.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto11.jpg" alt="" class="rounded-[18px]">
          </div>
        </div>

        <div class="flex flex-col gap-[13px]">
          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto8.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto10.jpg" alt="" class="rounded-[18px]">
          </div>

          <div class="border-dablue border p-2.5 rounded-[25px]">
            <img src="/src/assets/img/gphoto12.jpg" alt="" class="rounded-[18px]">
          </div>
        </div>


        <div class="absolute -top-[8%] left-[36%] right-[35.7%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[31.3%] left-[4%] right-[78.7%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[33.3%] left-[67%] right-[15%]">
          <img src="/src/assets/icons/gcircle_red.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[60.2%] left-[29%] right-[54%]">
          <img src="/src/assets/icons/gcircle_red.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[70%] left-[80%] right-[4%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>

        <div class="absolute top-[85%] left-[41.5%] right-[41.5%]">
          <img src="/src/assets/icons/gcircle_blue.svg" alt="" class="w-full">
        </div>
      </div>
    </div>



    <div v-if="!isOpenGallery" @click="openGallery" class="
      w-max
      m-auto
      p-1.25
      absolute
      inset-x-0
      -bottom-8
      border-[#C9185C] border
      rounded-[17px]
    ">
      <div class="
        bg-[#E05C92] hover:bg-[#4F7A23]/0
        text-[14px] text-center text-white font-semibold
        rounded-xl md:rounded-4xl
        transition-all duration-200
        cursor-pointer
        px-5.25 md:px-5 py-2 md:py-2

      ">
        ПОСМОТРЕТЬ ЕЩЁ
      </div>
    </div>

    <!-- <div class="absolute inset-x-0 top-[2%] -z-1">
      <img src="/src/assets/img/bg_gal.svg" alt="" class="m-auto">
    </div> -->
  </div>
</template>

<script setup>
import { ref } from 'vue';
import eventBus from '@/eventBus';

let isOpenGallery = ref(false)

function openGallery() {
  isOpenGallery.value = true
  eventBus.emit('openGallery', isOpenGallery.value) // To servicesSection
}

document.body.scrollTop = 0

</script>
