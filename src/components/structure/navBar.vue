<template>
  <nav class="
    fixed z-20
    left-0 right-0 top-0
    text-white
  " :class="changeBgNav ? 'bg-white/70 backdrop-blur-sm' : ''">
    <div class="xl:w-[1280px] xl:m-auto flex justify-between items-center px-3.5 md:px-4 xl:px-10 py-2 md:py-6" :class="changeBgNav ? 'lg:py-2' : '  xl:py-10 '">
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


      <div class="
        p-1.25
        border-[#C9185C] border
        rounded-full
      ">
        <a href="tel:+79171772625" class="
          flex gap-1.25

          bg-[#E05C92] hover:bg-[#4F7A23]/0
          text-[12px] text-center text-white hover:text-[#4F7A23]
          rounded-full md:rounded-4xl
          transition-all duration-200
          cursor-pointer
          px-3.5 md:px-5 py-1.5 md:py-2

        ">
          <img src="../../assets/icons/phone.svg" alt="" class="">
          +7 (917) 177-26-25
        </a>
      </div>

      
        <div @click="openMenu = !openMenu" class="lg:hidden border-[#C9185C] border rounded-[11px] px-2.25 py-3">
          <img src="../../assets/icons/burger.svg" alt="">
        </div>
      
<!-- 
      <div v-if="openMenu" @click="openMenu = !openMenu" class="lg:hidden">
        <svg width="30" height="22" viewBox="0 0 26 25" fill="none" xmlns="http://www.w3.org/2000/svg" class="md:w-[45px] md:h-[35px]">
          <path d="M1 24L25 1M1 1L25 24" stroke="black" stroke-width="3" stroke-linecap="round"/>
        </svg>
      </div> -->

      <transition>
        <div v-if="openMenu" class="
          lg:hidden
          absolute
          inset-0
          h-screen
          text-[15px] md:text-[24px]
          gap-1 md:gap-2
          p-3   
          bg-[#D3B9FF]
          duration-500 animate-opacity
        ">
          <div class="flex justify-between items-center">
            <div class="">
              <router-link to="/">
                <img src="../../assets/icons/main_logo_open_menu.svg" alt="" class="lg:hidden md:w-40 xl:w-[70px]">
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

            <div class="
              p-1.25
              border-[#C9185C] border
              rounded-full
            ">
              <a href="tel:+79171772625" class="
                flex gap-1.25

                bg-[#E05C92] hover:bg-[#4F7A23]/0
                text-[12px] text-center text-white hover:text-[#4F7A23]
                rounded-full md:rounded-4xl
                transition-all duration-200
                cursor-pointer
                px-3.5 md:px-5 py-1.5 md:py-2

              ">
                <img src="../../assets/icons/phone.svg" alt="" class="">
                +7 (917) 177-26-25
              </a>
            </div>

            <div @click="openMenu = !openMenu" class=" lg:hidden border-[#C9185C] border rounded-[11px] px-2.25 py-3">
              <img src="../../assets/icons/burger.svg" alt="">
            </div>
          </div>
        </div>
      </transition>
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
