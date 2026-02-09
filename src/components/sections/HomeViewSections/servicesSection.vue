<template>
  <div class="xl:w-[1280px] xl:m-auto px-2 md:px-4 xl:px-10">
    <div class=" flex mt-[40px] md:mt-[70px] items-center gap-3 md:gap-6">
      <div>
        <img src="@/assets/icons/logo_left_head.svg" alt="" class="md:w-20 lg:w-15">
      </div>

      <h2 class="text-[46px] md:text-[80px] lg:text-[65px] font-semibold">
      Наши услуги
      </h2>
    </div>

    <div class="
      mt-[22px] md:mt-[28px] 
      flex flex-col lg:flex-wrap  
      gap-2 md:gap-4 lg:gap-3
      text-white
    ">
      <div class="flex max-lg:flex-col lg:justify-between gap-2 md:gap-4 lg:gap-3">
        <template v-for="service in services" :key="service">
          <div v-if="service.id <= 3" class="
            relative 
            h-[172px] lg:h-[221px] 
            flex items-end lg:basis-1/3
            bg-[#4F7A23] 
            rounded-[20px] 
            p-5
          ">
            <div class="absolute right-0" :class="service.stylesDivImg">
              <img :src="service.img" alt="" :class="service.stylesImg">
            </div>

            <div class="">
              <div v-html="service.head" class="text-[20px] md:text-[30px] lg:text-[24px] font-semibold md:max-xl:w-full" :class="service.stylesHead">
              </div>

              <div class="md:text-[24px] lg:text-[18px]">
                {{service.text}}
              </div>
            </div>
          </div>
        </template>
      </div>

      <div class="flex max-lg:flex-col lg:justify-between gap-2 md:gap-4 lg:gap-3">
        <template v-for="service in services" :key="service">
          <div v-if="service.id > 3" class="
            relative 
            h-[172px] lg:h-[221px] 
            flex items-end lg:basis-1/3
            bg-[#4F7A23] 
            rounded-[20px] 
            p-5
          ">
            <div class="absolute right-0" :class="service.stylesDivImg">
              <img :src="service.img" alt="" :class="service.stylesImg">
            </div>

            <div class="">
              <div v-html="service.head" class="text-[20px] md:text-[30px] lg:text-[23px] font-semibold md:w-full" :class="service.stylesHead">
              </div>

              <div class="md:text-[24px] lg:text-[18px]">
                {{service.text}}
              </div>
            </div>
          </div>
        </template>
      </div>
      
    </div>
  </div>
</template>

<script setup>

let services = [
  {
    id: 1, 
    head: "Укладка <br class='max-lg:hidden'> тротуарной плитки",
    text: "прочные и стильные дорожки",
    img: new URL('@/assets/icons/paving_slab.svg', import.meta.url).href,
    stylesHead: "w-[190px] lg:w-max",
    stylesDivImg: "top-[18px]",
    stylesImg: "lg:w-[95px]"
  },
  {
    id: 2,
    head: "Монтаж террас",
    text: "уютные зоны для отдыха",
    img: new URL('@/assets/icons/terrace.svg', import.meta.url).href,
    stylesHead: "w-[190px] lg:w-[220px]",
    stylesDivImg: "bottom-0",
    stylesImg: "lg:w-[91px]"
  },
  {
    id: 3,
    head: "Системы водоотведения",
    text: "защита участка от влаги",
    img: new URL('@/assets/icons/tube.svg', import.meta.url).href,
    stylesHead: "w-[220px]",
    stylesDivImg: "top-0",
    stylesImg: "lg:w-[112px]"
  },
  {
    id: 4,
    head: "Монтаж <br class='md:hidden'> зон отдыха <br class='max-lg:hidden'> и пергол",
    text: "создание уюта и эстетики",
    img: new URL('@/assets/icons/pergola.svg', import.meta.url).href,
    stylesHead: "w-[220px] lg:w-[270px]",
    stylesDivImg: "bottom-0",
    stylesImg: "lg:w-[71px]"
  },
  {
    id: 5,
    head: "Вертикальное <br class='max-lg:hidden'> планирование участка",
    text: "подготовка территории",
    img: new URL('@/assets/icons/ruler.svg', import.meta.url).href,
    stylesHead: "w-[230px]  xl:w-[350px]",
    stylesDivImg: "top-[10px]",
    stylesImg: "lg:w-[104px]"
  },
  {
    id: 6,
    head: "Монтаж <br class='md:max-lg:hidden'> уличного освещения",
    text: "комфортные прогулки",
    img: new URL('@/assets/icons/flashlight.svg', import.meta.url).href,
    stylesHead: "w-[200px] lg:w-[280px]",
    stylesDivImg: "bottom-0",
    stylesImg: "lg:w-[121px]"
  },
]
</script>