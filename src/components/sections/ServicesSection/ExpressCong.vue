<template>
  <div class="mt-[33px] text-[14px] flex flex-col gap-[23px]">
    <div class="border-dapink border rounded-[40px] p-[3.5%]">
      <div class="flex flex-col gap-[13px] bg-liliblue rounded-4xl px-[8.5%] py-[5%] ">
        <div class="text-[17px] font-semibold text-center">
          ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ
        </div>

        <div class="text-center">
          (10-30 МИНУТ)
        </div>

        <div class="border-dablue border rounded-full px-[5%] py-[3%] text-center font-semibold text-dablue">
          2600/3200 РУБ + ТАКСИ
        </div>

        <div class="text-center font-semibold text-dablue">
          НАЖМИТЕ, <br> ЧТОБЫ УЗНАТЬ БОЛЬШЕ
        </div>
      </div>
    </div>

    <div class="backdrop-blur-xs leading-6 border-dapink border rounded-[30px] py-[5%] px-[7%]">
      Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать яркие поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным
    </div>

    <div class="backdrop-blur-xs leading-6 border-dapink border rounded-[30px] py-[5%] px-[7%]">
      Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту
    </div>

    <div class="border-dapink border rounded-[29px] p-[2%]">
      <div class="flex flex-col gap-[13px] bg-lipink rounded-[24px] px-[5%] py-[4%] ">
        <div class=" text-center text-white">
          ПОСМОТРЕТЬ ПЕРСОНАЖЕЙ ДЛЯ ЭТОЙ УСЛУГИ
        </div>
      </div>
    </div>

    <div>
      <div class="border-dapink border rounded-[40px] p-[4%]">
        <div>
          <img src="/src/assets/img/dandelion_sm.jpg" alt="" class="rounded-4xl w-full">
        </div>
      </div>

      <div class="text-[20px] font-semibold mt-2">
        ЗАЙЧИК-ОДУВАНЧИК
      </div>
    </div>

    <div>
      <div class="border-dapink border rounded-[40px] p-[4%]">
        <div>
          <img src="/src/assets/img/marshmallows_sm.jpg" alt="" class="rounded-4xl w-full">
        </div>
      </div>

      <div class="text-[20px] font-semibold mt-2">
        ЗАЙКА-ЗЕФИРКА
      </div>
    </div>

    <div>
      <div class="border-dapink border rounded-[40px] p-[4%]">
        <div>
          <img src="/src/assets/img/snowflake_sm.jpg" alt="" class="rounded-4xl w-full">
        </div>
      </div>

      <div class="text-[20px] font-semibold mt-2">
        ЗАЙКА-СНЕЖИНКА
      </div>
    </div>

    <div>
      <div class="border-dapink border rounded-[40px] p-[4%]">
        <div>
          <img src="/src/assets/img/zephyr_sm.jpg" alt="" class="rounded-4xl w-full">
        </div>
      </div>

      <div class="text-[20px] font-semibold mt-2">
        ЗЕФИР-ЗАЙЦЕВИЧ
      </div>
    </div>

    <div v-if="!isOpenCharacters" @click="openGallery" class="
      p-1.25
      -bottom-8
      border-[#C9185C] border
      rounded-[20px]
    ">
      <div class="
        bg-[#E05C92] hover:bg-[#4F7A23]/0
        text-[14px] text-center text-white
        rounded-2xl md:rounded-4xl
        transition-all duration-200
        cursor-pointer
        px-5.25 md:px-5 py-2.5 md:py-2
      ">
        ПОСМОТРЕТЬ ЕЩЁ
      </div>
    </div>

    <orderBlock />
  </div>
</template>

<script setup>
import { ref } from 'vue';

import orderBlock from '@/components/structure/orderBlock.vue';

let isOpenCharacters = ref(false)
</script>
