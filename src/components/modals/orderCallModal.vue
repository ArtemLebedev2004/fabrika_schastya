<template>
    <div class="
      fixed inset-0 z-40
      flex justify-center items-center
    ">
      <div class="relative w-[80%] lg:w-[60%] xl:w-[50%] max-w-[700px] bg-[#4F7A23] rounded-[20px] md:rounded-[30px] p-5 md:p-8 lg:p-12">
        <div @click="$emit('closeModal')" class="
          w-12 h-12 md:w-20 md:h-20 
          absolute z-40 
          -top-14 md:-top-22 lg:top-0
          right-0 lg:-right-24
          bg-[#4F7A23] hover:bg-white
          transition-all duration-100
          rounded-[10px] md:rounded-[14px] 
          flex justify-center items-center 
          cursor-pointer
          group
        ">
          <svg width="30" height="22" viewBox="0 0 26 25" fill="none" xmlns="http://www.w3.org/2000/svg" class="md:w-14 md:h-11">
            <path d="M1 24L25 1M1 1L25 24" stroke="white" stroke-width="3" stroke-linecap="round" class="group-hover:stroke-[#4F7A23]"/>
          </svg>
        </div>
        
        <div class="text-center text-white text-[20px] md:text-[30px] xl:text-[28px]">
            Заказ звонка
        </div>

        <form action="https://formspree.io/f/xblgawon" method="POST" class="mt-5 md:mt-8 text-[15px] md:text-[24px] xl:text-[20px] relative z-10">
          <input v-model="inputName" type="text" name="Имя" class="
            w-full 
            border-2 xl:border-3 border-white 
            rounded-full 
            py-2 md:py-4 px-4 md:px-8 
            outline-none 
            text-white
          " placeholder="Ваше имя">
          <div v-if="!inputName && isClick" class="text-red-400">
            Вы ничего не ввели
          </div>

          <input v-model="inputPhone" type="phone" name="Телефон" class="
            w-full 
            border-2 xl:border-3 border-white 
            rounded-full 
            py-2 md:py-4 px-4 md:px-8 
            mt-3 md:mt-5 
            outline-none 
            text-white
          " placeholder="Ваш телефон">
          <div v-if="!inputPhone && isClick" class="text-red-400">
            Вы ничего не ввели
          </div>

          <div class="group mt-4 md:mt-8">
              <input v-model="inputCheckbox" id="check_circle" type="checkbox" class="hidden">
              
              <div class="flex gap-3 md:gap-6 xl:gap-3 items-center ">
                <label for="check_circle" class="cursor-pointer">
                  <div class="
                    w-4 h-4 md:w-8 md:h-8 xl:w-6 xl:h-6 
                    rounded-full 
                    border-2 xl:border-3 border-white 
                    group-has-checked:bg-white
                  "></div>                  
                </label>

                <div class="w-fit max-md:text-[13px] text-white leading-5 md:leading-7">Даю <router-link to="/user_agreement" class="underline">согласие на обработку</router-link> своих персональных данных</div>
              </div>

              <div v-if="!inputCheckbox && isClick" class="text-red-400">
                Вы не отметили
              </div>
          </div>

          <button @click="checkForm" :type="isSubmit ? 'submit' : 'button'" class="
            w-full 
            py-3 md:py-4 xl:py-3 
            text-center text-[#4F7A23] hover:text-white
            rounded-full 
            bg-white hover:bg-black/0
            mt-7 md:mt-10  
            xl:border-5 border-white 
            transition-all duration-200   
            cursor-pointer
          ">
            Заказать звонок
          </button>
        </form>

        <div>
            <img src="@/assets/icons/logo_bg.svg" alt="" class="w-30 md:w-50 z-0 absolute right-0 bottom-0">
        </div>
      </div>
        
    </div>   
    
    <div class="fixed inset-0 bg-gray-400/75 z-30"></div>
</template>

<script setup>
import { ref,  watch } from 'vue';

let inputName = ref('')
let inputPhone = ref('')
let inputCheckbox = ref(false)

let isClick = ref(false)
let isSubmit = ref(false)

function checkForm() {
  isClick.value = true

  if (inputName.value && inputPhone.value && inputCheckbox.value) {
    isSubmit.value = true
  }
}

watch(inputName, async (newValue) => {
    if (newValue == ' ') {
      inputName.value = ''
    } else if (newValue.indexOf('  ') > -1) {
      inputName.value = inputName.value.replace('  ', ' ')
    } else if (newValue.indexOf(' |') > -1) {
      inputName.value = inputName.value.replace(' |', '|')
    } 
})
</script>