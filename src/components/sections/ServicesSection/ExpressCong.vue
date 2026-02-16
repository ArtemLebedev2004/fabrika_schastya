<template>
  <transition>
    <div v-if="isOpenDolls" class="text-[14px] flex flex-col gap-[23px]">
      <serviceBlock @click="isOpenCong = !isOpenCong" 
        title="ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ"
        time="(10-30 МИНУТ)"
        price="2600/3200 РУБ + ТАКСИ"
      />

      <transition>
        <div v-if="isOpenCong" class="flex flex-col gap-[23px]">
          <TextBlock
            text="Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать яркие поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным"
          />
          
          <TextBlock
            text="Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту"
          />
          
          <div @click="isOpenCharacters = !isOpenCharacters" class="border-dapink border rounded-[29px] p-[2%]">
            <div class="flex flex-col gap-[13px] bg-lipink rounded-[24px] px-[5%] py-[4%] ">
              <div class=" text-center text-white">
                ПОСМОТРЕТЬ ПЕРСОНАЖЕЙ ДЛЯ ЭТОЙ УСЛУГИ
              </div>
            </div>
          </div>

          <transition name="open-characters">
            <div v-if="isOpenCharacters" class="flex flex-col gap-[23px]">
              <ServicePhotoBlock
                img="/src/assets/img/dandelion_sm.jpg"
                text="ЗАЙЧИК-ОДУВАНЧИК"
              />

              <ServicePhotoBlock
                img="/src/assets/img/marshmallows_sm.jpg"
                text="ЗАЙКА-ЗЕФИРКА"
              />
              
              <ServicePhotoBlock
                img="/src/assets/img/snowflake_sm.jpg"
                text="ЗАЙКА-СНЕЖИНКА"
              />

              <ServicePhotoBlock
                img="/src/assets/img/zephyr_sm.jpg"
                text="ЗЕФИР-ЗАЙЦЕВИЧ"
              />

              <ServicePhotoBlock
                img="/src/assets/img/pups_boy_sm.jpg"
                text="ПУПС МАЛЬЧИК - МИРОН"
              />

              <ServicePhotoBlock
                img="/src/assets/img/pups_girl_sm.jpg"
                text="ПУПС ДЕВОЧКА - ЕВА"
              />

              <ServicePhotoBlock
                img="/src/assets/img/doll_lol_sm.jpg"
                text="КУКЛА ЛОЛ"
              />

              <ServicePhotoBlock
                img="/src/assets/img/minion_sm.jpg"
                text="МИНЬОН"
              />
            </div>
          </transition>        

          <orderBlock />
        </div>
      </transition>
      
     
    </div>
  </transition>
  
</template>

<script setup>
import { ref } from 'vue';
import { toRefs } from 'vue';

import orderBlock from '@/components/structure/orderBlock.vue';
import TextBlock from '@/components/structure/textBlock.vue';
import ServicePhotoBlock from '@/components/structure/servicePhotoBlock.vue';
import serviceBlock from './serviceBlock.vue';

let props = defineProps(['isOpenDolls'])

const { isOpenDolls } = toRefs(props)

let isOpenCong = ref(false)

let isOpenCharacters = ref(false)
</script>

<style scoped>
.v-enter-active,
.v-leave-active,
.open-characters-enter-active,
.open-characters-leave-active {
  transition: all 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  transform: translateX(-100vw);
}

.open-characters-enter-from,
.open-characters-leave-to {
  opacity: 0
}

</style>