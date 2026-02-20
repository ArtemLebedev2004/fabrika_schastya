<template>
  <div class="relative ">
    <div class="relative max-lg:max-w-[450px] xl:w-[1280px] m-auto px-4.5 md:px-4 xl:px-10 "
         :class="isOpenGallery ? 'mt-[70px]' : 'mt-[81px]'">
      <h2 class="
        font-[Soroka] text-liblue
        text-[50px] md:text-[85px] lg:text-[63px]
        leading-none
      ">
        НАШИ <br> УСЛУГИ
      </h2>

      <TextBlockSmall text="Мы предлагаем широкий спектр способностей, которые сделают Ваш праздник незабываемым" />

      <div class="mt-9.5 flex flex-col gap-8.5">
        <typeServiceBlock v-for="service in servicesArr" :key="service.id"
          :service=service
        />
        
        <ExpressCong :isOpenDolls=isClickOnDolls />

        <div>
          <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
              fill="#C9185C"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
              <img src="/src/assets/img/serv_photo2.png" alt="" class="w-full h-full">
            </div>

            <div class="absolute right-0 left-[83.7%] -top-[7.8%]">
              <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                stroke="#C9185C"/>
              </svg>

              <div class="absolute inset-[15%] bg-lipink rounded-full flex items-center p-[16%]">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block  w-full">
              </div>
            </div>
          </div>

          <div class="text-[20px] font-semibold mt-2 leading-6">
            АНИМАЦИОННЫЕ ПЕРСОНАЖИ
          </div>
        </div>

        <div>
          <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
              fill="#C9185C"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
              <img src="/src/assets/img/serv_photo3.png" alt="" class="w-full h-full">
            </div>

            <div class="absolute right-0 left-[83.7%] -top-[7.8%]">
              <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                stroke="#C9185C"/>
              </svg>

              <div class="absolute inset-[15%] bg-lipink rounded-full flex items-center p-[16%]">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block  w-full">
              </div>
            </div>
          </div>

          <div class="text-[20px] font-semibold mt-2">
            ПАТИ И КВЕСТЫ
          </div>
        </div>

        <div>
          <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
              fill="#C9185C"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
              <img src="/src/assets/img/serv_photo4.png" alt="" class="w-full h-full">
            </div>

            <div class="absolute top-[11%] left-[8%] text-[14px] text-white bg-dablue px-[11px] py-[3px] rounded-full shadow-[4px_4px_4px_rgba(0,0,0,0.15)]">
              new
            </div>

            <div class="absolute right-0 left-[83.7%] -top-[7.8%]">
              <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                stroke="#C9185C"/>
              </svg>

              <div class="absolute inset-[15%] bg-lipink rounded-full flex items-center p-[16%]">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block  w-full">
              </div>
            </div>
          </div>

          <div class="text-[20px] font-semibold mt-2 leading-6">
            МОБИЛЬНЫЙ ПЛАНЕТАРИЙ
          </div>
        </div>

        <div>
          <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
              fill="#C9185C"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
              <img src="/src/assets/img/serv_photo5.png" alt="" class="w-full h-full">
            </div>

            <div class="absolute right-0 left-[83.7%] -top-[7.8%]">
              <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                stroke="#C9185C"/>
              </svg>

              <div class="absolute inset-[15%] bg-lipink rounded-full flex items-center p-[16%]">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block  w-full">
              </div>
            </div>
          </div>

          <div class="text-[20px] font-semibold mt-2 leading-6">
            ЯРМАРКА РАЗВЛЕЧЕНИЙ
          </div>
        </div>

        <div>
          <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
              fill="#C9185C"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
              <img src="/src/assets/img/serv_photo6.png" alt="" class="w-full h-full">
            </div>

            <div class="absolute right-0 left-[83.7%] -top-[7.8%]">
              <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                stroke="#C9185C"/>
              </svg>

              <div class="absolute inset-[15%] bg-lipink rounded-full flex items-center p-[16%]">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block  w-full">
              </div>
            </div>
          </div>

          <div class="text-[20px] font-semibold mt-2 leading-6">
            ДОПОЛНЕНИЯ
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import eventBus from '@/eventBus';
import { ref } from 'vue';

import ExpressCong from '../ServicesSection/ExpressCong.vue';
import TextBlockSmall from '@/components/structure/textBlockSmall.vue';
import typeServiceBlock from '../ServicesSection/typeServiceBlock.vue';

let isClickOnDolls = ref(false)
let isOpenGallery = ref(false)
// let isOpenDolls = ref(false)

eventBus.on('openGallery', (data) => {            // from gallerySection
  isOpenGallery.value = data
})

document.body.scrollTop = 0

let servicesArr = [

  {
    id: 1,
    titleTypeService: 'РОСТОВЫЕ КУКЛЫ',
    serveTypePhoto: '/src/assets/img/serv_photo1.png',
    menuText1: 'УСЛУГИ',
    menuText2: 'ПЕРСОНАЖИ',
    menuText3: 'ЗАКАЗАТЬ',
    services: {
      cong: {
        titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
        timeService: '(10-30 минут)',
        priceService: '2600/3200 РУБ + ТАКСИ'
      },   
    }
  },

  // animators: {
  //   id: 2,
  //   titleTypeService: 'АНИМАЦИОННЫЕ ПЕРСОНАЖИ',
  //   menuText1: 'УСЛУГИ',
  //   menuText2: 'ПЕРСОНАЖИ',
  //   menuText3: 'ЗАКАЗАТЬ'
  // },

  // party: {
  //   id: 3,
  //   titleTypeService: 'ПАТИ И КВЕСТЫ',
  //   menuText1: 'УСЛУГИ',
  //   menuText2: 'ЗАКАЗАТЬ',
  // },

  // planetarium: {
  //   id: 4,
  //   titleTypeService: 'МОБИЛЬНЫЙ ПЛАНЕТАРИЙ',
  //   menuText1: 'УСЛУГИ',
  //   menuText2: 'ПЕРСОНАЖИ',
  //   menuText3: 'ЗАКАЗАТЬ'
  // }
]

</script>

<style scoped>
</style>