<template>
  <div class="relative max-lg:max-w-[450px] xl:w-[1280px] m-auto px-4.5 md:px-4 xl:px-10 ">
    <div class="lg:flex mt-[100px] md:mt-[170px] lg:mt-40 xl:mt-50 lg:gap-10">
      <div class="lg:relative lg:basis-1/2 lg:flex lg:flex-col  lg:justify-between">
        <div class="m-auto">
          <h1 id="observe_h1" class=" dsfdsg
            font-[Soroka] text-[#E05C92]
            text-[45px] md:text-[85px] lg:text-[63px]
            leading-none
          ">
            Фабрика
          </h1>

          <div class="
          font-[Soroka] text-[#E05C92]
          text-[45px] md:text-[85px] lg:text-[63px]
          leading-none
          text-right
          ">Счастья</div>

          <div class="absolute left-4.5 leading-6.5 text-[19.5px] text-[#E05C92] font-semibold mt-3.5">
            Организация праздников, ярмарок и вечеринок
            <img src="/src/assets/icons/petard.svg" alt="" class="absolute top-[29px] left-[280px]">
          </div>

          <div class="text-[14.5px] font-light mt-[81px]">
            Креативно поздравим родственников и коллег. Украсим вашу Свадьбу, Юбилей, Новый год, Выпускной и другие торжества
          </div>

          <div class="relative mt-[23px]">
            <img src="/src/assets/icons/rect_main_photo.svg" alt="" class="w-full">

            <div class="absolute inset-3">
              <img src="/src/assets/img/main_photo.png" alt="" class="w-full">
            </div>

            <div class="absolute right-0 left-[85.5%] top-[3px]">
                <img src="/src/assets/icons/ellipse_main_photo.svg" alt="" class="w-full">

                <!-- <div class="bg-[#AD74E9] p-[10px]">
                  <img src="/src/assets/icons/arrow_right.svg" alt="" class="min-w-[19px]">


                </div> -->
            </div>
          </div>
        </div>


        <div @click="openModal = !openModal" class="
          max-lg:hidden
          relative
          bottom-0
          w-full
          text-[25px] text-white text-center
          bg-[#4F7A23]
          rounded-4xl md:rounded-[100px]
          mt-[18px] md:mt-[25px] xl:mt-0
          py-5 hover:py-6
          border-[#4F7A23]
          transition-all duration-200
          cursor-pointer
          overflow-hidden
          before:content-['']
          before:animate-hologram
          before:block
          before:-rotate-45
          before:absolute
          before:-top-[120%]
          before:-left-[100%]
          before:w-[200%]
          before:h-[70%]
          before:bg-linear-to-b
          before:from-green-100/20
          before:bg-transparent
        ">
          Заказать звонок
        </div>
      </div>

      <div class="relative lg:flex lg:items-center mt-[20px] md:mt-[45px] lg:mt-0 lg:basis-1/2 p-3 md:p-6">
        <img src="@/assets/img/main_img.jpg" alt="" class="w-full m-auto rounded-[20px] md:rounded-[40px] lg:rounded-[24px]">
        <div class="absolute inset-0 rounded-[20px] md:rounded-[40px] lg:rounded-[30px] border-6 md:border-12 lg:border-10 border-[#4F7A23] animate-swim-border"></div>

      </div>
    </div>


    <div class="lg:hidden text-center mt-[18px] md:mt-[25px] text-[20px] md:text-[30px]">
      Гарантия 1 год
    </div>

    <div @click="openModal = !openModal" class="
      button
      overflow-hidden
      lg:hidden
      relative z-10
      text-[20px] md:text-[30px] text-white text-center
      bg-[#4F7A23]
      rounded-4xl md:rounded-[100px]
      mt-[18px] md:mt-[25px]
      py-4 md:py-8
      before:content-['']
      before:animate-hologram
      before:block
      before:-rotate-45
      before:bg-black
      before:absolute
      before:-top-[120%]
      before:-left-[100%]
      before:w-[200%]
      before:h-[70%]
      before:bg-linear-to-b
      before:from-green-100/20
      before:bg-transparent
    ">
      Заказать звонок
    </div>
  </div>

  <OrderCallModal v-if="openModal" @closeModal='openModal = false'/>

</template>

<script setup>
import { ref } from 'vue';
import OrderCallModal from '../../modals/orderCallModal.vue';

document.body.scrollTop = 0

let openModal = ref(false)

</script>
