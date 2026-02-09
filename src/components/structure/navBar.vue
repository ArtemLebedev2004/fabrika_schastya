<template>
  <nav class="
    fixed z-20
    left-0 right-0 top-0  
    text-white 
  " :class="changeBgNav ? 'bg-white/70 backdrop-blur-sm' : ''">
    <div class="xl:w-[1280px] xl:m-auto flex justify-between items-center px-2 md:px-4 xl:px-10 py-2 md:py-6" :class="changeBgNav ? 'lg:py-2' : '  xl:py-10 '">
      <div>
        <router-link to="/">
          <img src="../../assets/icons/main_logo_sm.svg" alt="" class="lg:hidden md:w-40 xl:w-[70px]">
          <img src="../../assets/icons/main_logo.svg" alt="" class="max-lg:hidden md:w-40 lg:w-18 xl:w-20">
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
        flex flex-col md:flex-row items-center
        text-[15px] md:text-[24px] lg:text-[18px] 
        gap-1 md:gap-5
      ">
        <div class="text-black">+7-800-700-30-08</div>
        <div class="
          max-md:w-full
        ">
          <a href="tel:+78007003008" class="
            block
            max-md:w-full 
            bg-[#4F7A23] hover:bg-[#4F7A23]/0
            text-center text-white hover:text-[#4F7A23]
            rounded-2xl md:rounded-4xl 
            transition-all duration-200   
            cursor-pointer 
            px-3 md:px-5 py-1.5 md:py-2 
            border-[#4F7A23] xl:border-5
          ">Позвонить</a>
        </div>
      </div>

      <div v-if="!openMenu" @click="openMenu = !openMenu" class="animate-opacity lg:hidden">
        <svg width="30" height="22" viewBox="0 0 20 14" fill="none" xmlns="http://www.w3.org/2000/svg" class="md:w-[45px] md:h-[35px]">
          <path d="M1 1H19M1 7H19M1 13H19" stroke="black" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>

      <div v-if="openMenu" @click="openMenu = !openMenu" class="animate-opacity lg:hidden">
        <svg width="30" height="22" viewBox="0 0 26 25" fill="none" xmlns="http://www.w3.org/2000/svg" class="md:w-[45px] md:h-[35px]">
          <path d="M1 24L25 1M1 1L25 24" stroke="black" stroke-width="3" stroke-linecap="round"/>
        </svg>
      </div>

      <transition>
        <div v-if="openMenu" class="
          lg:hidden
          absolute 
          right-2 top-20 md:top-35 
          text-[15px] md:text-[24px] 
          flex flex-col items-end 
          gap-1 md:gap-2 
          p-3 
          border-2 border-[#4F7A23] 
          rounded-[20px] 
          bg-white/50  
          transition-opacity duration-500 animate-opacity
        ">
          <div class="py-2 px-4 md:px-7 bg-[#4F7A23] rounded-3xl">
            <router-link to="/#services" v-scroll-to="'#services'">Услуги</router-link>
          </div>
          <div class="py-2 px-4 md:px-7 bg-[#4F7A23] rounded-3xl">
            <router-link to="/#projects" v-scroll-to="'#projects'">Проекты</router-link>
          </div>
          <div class="py-2 px-4 md:px-7 bg-[#4F7A23] rounded-3xl">
            <router-link to="/#about" v-scroll-to="'#about'">О нас</router-link>
          </div>
          <div class="py-2 px-4 md:px-7 bg-[#4F7A23] rounded-3xl">
            <router-link to="/#contacts" v-scroll-to="'#contacts'">Контакты</router-link>
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
  opacity: 1;
}
.v-leave-to {
  opacity: 0;
}
</style>