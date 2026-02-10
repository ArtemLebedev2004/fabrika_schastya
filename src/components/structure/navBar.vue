<template>
  <nav class="
    fixed z-20
    left-0 right-0 top-0
    text-white
  " :class="changeBgNav ? 'bg-white/70 backdrop-blur-sm' : ''">
    <div class="xl:w-[1280px] xl:m-auto flex justify-between items-center px-4.5 md:px-4 xl:px-10 py-4 md:py-6" :class="changeBgNav ? 'lg:py-2' : '  xl:py-10 '">
      <div>
        <router-link to="/">
          <img src="../../assets/icons/main_logo.svg" alt="" class="lg:hidden md:w-40 xl:w-[70px]">
        </router-link>
      </div>

      <div class="max-lg:hidden lg:flex text-[18px] gap-14 xl:gap-20 text-black ">
        <div>
          <router-link to="/#services" v-scroll-to="'#services'" class="transition-all duration-75 hover:border-b-5 border-[#4F7A23] pb-2">Услуги</router-link>
        </div>

        <div class="">
          <router-link to="/#projects" v-scroll-to="'#projects'" class="transition-all duration-75 hover:border-b-5 border-[#4F7A23] pb-2">Проекты</router-link>
        </div>

        <div>
          <router-link to="/#about" v-scroll-to="'#about'" class="transition-all duration-75 hover:border-b-5 border-[#4F7A23] pb-2">О нас</router-link>
        </div>

        <div>
          <router-link to="/#contacts" v-scroll-to="'#contacts'" class="transition-all duration-75 hover:border-b-5 border-[#4F7A23] pb-2">Контакты</router-link>
        </div>
      </div>


      <a href="tel:+79171772625" class="
        p-1.25
        border-[#C9185C] border
        rounded-full
      ">
        <div class="
          flex gap-1.25

          bg-[#E05C92] hover:bg-[#4F7A23]/0
          text-[14px] text-center text-white hover:text-[#4F7A23]
          rounded-full md:rounded-4xl
          transition-all duration-200
          cursor-pointer
          px-3.5 md:px-5 py-1.5 md:py-2

        ">
          +7 (917) 177-26-25
        </div>
      </a>


      <div @click="openMenu = !openMenu" class="lg:hidden border-[#C9185C] border rounded-[11px] px-2.5 py-3.25">
        <img src="../../assets/icons/burger.svg" alt="">
      </div>

      <div class="
        lg:hidden
        absolute
        inset-0
        h-screen
        text-[15px] md:text-[24px]
        gap-1 md:gap-2
        bg-[#D3B9FF]
        transition duration-500 ease-in-out
        -translate-x-full
        px-4.5
      "
      :class="openMenu ? 'translate-x-0' : ''">
        <div class="flex justify-between items-center py-4">
          <div class="">
            <router-link to="/">
              <img src="../../assets/icons/main_logo_open_menu.svg" alt="" class="w-[58px] lg:hidden md:w-40 xl:w-[70px]">
            </router-link>
          </div>

          <a href="tel:+79171772625" class="
            p-1.25
            border-[#654ADE] border
            rounded-full
          ">
            <div class="
              flex gap-1.25

              bg-[#9881FF] hover:bg-[#4F7A23]/0
              text-[14px] text-center text-white
              rounded-full md:rounded-4xl
              transition-all duration-200
              cursor-pointer
              px-3.5 md:px-5 py-1.5 md:py-2

            ">
              +7 (917) 177-26-25
            </div>
          </a>

          <div @click="openMenu = !openMenu" class="w-[48px] h-[44px] border-[#654ADE] border rounded-[11px] p-1.25">
            <div class="bg-[#9881FF] h-full px-2.5 py-2 rounded-[7px] text-center">
              <svg width="16" viewBox="0 0 26 25" fill="none" xmlns="http://www.w3.org/2000/svg" class="md:w-[45px] md:h-[35px]">
                <path d="M1 24L25 1M1 1L25 24" stroke="white" stroke-width="3" stroke-linecap="round"/>
              </svg>
            </div>
          </div>
        </div>


        <div class="w-max relative m-auto flex flex-col items-center justify-center mt-[101px] text-[16px] font-light gap-8 xl:gap-20 text-black ">
          <router-link to="/#services" v-scroll-to="'#services'" class=" w-65 h-max text-center py-4.25 leading-none rounded-full border-[#654ADE] border">
            Услуги
          </router-link>

          <router-link to="/#services" v-scroll-to="'#services'" class=" w-65 h-max text-center py-4.25 leading-none rounded-full border-[#654ADE] border">
            Товары
          </router-link>

          <router-link to="/#services" v-scroll-to="'#services'" class=" w-65 h-max text-center py-4.25 leading-none rounded-full border-[#654ADE] border">
            Творим добро
          </router-link>

          <router-link to="/#services" v-scroll-to="'#services'" class=" w-65 h-max text-center py-4.25 leading-none rounded-full border-[#654ADE] border">
            Наша команда
          </router-link>

          <div class="absolute w-[79px] h-[79px] -left-[40px] top-[19px] rounded-full border-[#654ADE] border"></div>
          <div class="absolute w-[79px] h-[79px] -right-[40px] top-[92px] rounded-full border-[#654ADE] border"></div>
          <div class="absolute w-[79px] h-[79px] -left-[40px] top-[167px] rounded-full border-[#654ADE] border"></div>

        </div>

        <div class="flex justify-center gap-[27px] mt-[51px]">
          <img src="../../assets/icons/vk.svg" alt="" class="">
          <img src="../../assets/icons/wa.svg" alt="" class="">
          <img src="../../assets/icons/tg.svg" alt="" class="">
          <img src="../../assets/icons/max.svg" alt="" class="">
        </div>

      </div>

    </div>
  </nav>

</template>

<script setup>
import router from '@/router';
import { nextTick, onMounted, ref } from 'vue';

let openMenu = ref(false)

let changeBgNav = ref(false)

onMounted(() => {
  const section = router.currentRoute.value.hash.replace("#", "")

  if (section) {
    nextTick(() => window?.document?.getElementById(section)?.scrollIntoView())
  }

  observeMainNav()
})

function observeMainNav() {
  let observe_h1 = document.getElementsByTagName('h1')[0]

  let rootMarginMain = null

  if (observe_h1.offsetTop != 0) {
    rootMarginMain = '-' + (observe_h1.clientHeight + observe_h1.offsetTop - 10) + 'px 0px 0px 0px'
  } else {
    rootMarginMain = '-' + (observe_h1.clientHeight + 110) + 'px 0px 0px 0px'
  }

  let observerBgNav = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (!entry.isIntersecting) {
      changeBgNav.value = 50
      console.log(rootMarginMain)
    } else {
      changeBgNav.value = 0
    }
  });
  }, { rootMargin: rootMarginMain });

  observerBgNav.observe(observe_h1);
}
</script>

<style>
.v-leave-from {
  width: 100%;
}
.v-leave-to {
  width: 0;
}
</style>
