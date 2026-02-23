<template>
    <div @click="swimBlur()">
        <div class="relative ">
            <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
                :fill="isOpenDolls ? '#397BD8' : '#C9185C'"/>
            </svg>

            <div class="absolute inset-x-[4%] inset-y-[6.5%]">
                <img :src="service.serveTypePhoto" alt="" class="w-full h-full rounded-4xl min-[415px]:rounded-[36px]">

                <transition>
                    <div v-if="isClickOnDolls" class="absolute -inset-[0.5%] ">
                        <svg @click="isClickOnBlur = true" width="100%" height="100%" viewBox="0 0 311 172" fill="none" xmlns="http://www.w3.org/2000/svg">
                          <foreignObject x="-11" y="-11" width="333" height="194"><div xmlns="http://www.w3.org/1999/xhtml" style="backdrop-filter:blur(5.5px);clip-path:url(#bgblur_0_1361_57_clip_path);height:100%;width:100%"></div></foreignObject><path data-figma-bg-blur-radius="11" d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z" fill="#FFD4DF" fill-opacity="0.69"/>
                          <defs>
                          <clipPath id="bgblur_0_1361_57_clip_path" transform="translate(11 11)"><path d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z"/>
                          </clipPath></defs>
                        </svg>

                        <div  class="absolute p-4 w-max h-[85%] m-auto inset-0 text-center text-dablue text-[17px] font-semibold flex flex-col justify-between items-center">
                          <div v-for="menuText in service.menuTexts" :key="menuText" @click="isClickMenu = menuText" class="relative w-max">
                            <div class="relative z-1">
                              {{ menuText }}
                            </div>

                            <div v-if="isClickMenu == menuText" class="absolute -inset-x-1 top-[50%] bottom-0 bg-pink-line-text rounded-full z-0">

                            </div>
                          </div>
                        </div>
                    </div>
                </transition>

                <!-- <blurPhoto
                  :isClickOnDolls="isClickOnDolls"
                  @isClickOnBlur="isClickOnBlur = true"
                /> -->
            </div>

            <div @click="isClickOnArrow = true" class="absolute right-0 left-[83.7%] -top-[7.8%]">
                <svg viewBox="0 0 66 66" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M11.5454 8.32934C25.0083 -3.34946 45.5044 -1.78569 57.3233 11.8387C69.1422 25.4631 67.7961 45.9747 54.3333 57.6535C40.8704 69.3323 20.3743 67.7685 8.55536 54.1441C-3.26361 40.5197 -1.91753 20.0082 11.5454 8.32934Z"
                :stroke="isOpenDolls ? '#397BD8' : '#C9185C'"/>
                </svg>

                <div class="absolute inset-[15%] rounded-full flex items-center p-[16%]" :class="isOpenDolls ? 'bg-liblue' : 'bg-lipink'">
                <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                <img src="/src/assets/icons/arrow_right.svg" alt="" class="block w-full transition-all duration-150" :class="isOpenDolls ? ' rotate-180' : ''">
                </div>
            </div>
        </div>

        <div class="text-[20px] font-semibold mt-2">
        {{service.titleTypeService}}
        </div>
    </div>


    <transition>
      <div v-if="isClickOnDolls && isClickMenu == 'УСЛУГИ'" class="text-[14px] flex flex-col gap-[23px]">
        <div v-for="insideService in service.services" :key="insideService">
          <div  @click="isClickServiceId.indexOf(insideService.id) != -1 ? isClickServiceId.splice(isClickServiceId.indexOf(insideService.id), 1) : isClickServiceId.push(insideService.id)" class="border-dapink border rounded-[40px] p-[3.5%]">
            <div class="flex flex-col gap-[13px] bg-liliblue rounded-4xl px-[8.5%] py-[5%] ">
              <div class="text-[17px] font-semibold text-center">
                {{insideService.titleService}}
              </div>

              <div class="text-center">
                {{insideService.timeService}}
              </div>

              <div class="border-dablue border rounded-full px-[4.5%] py-[3%] text-center font-semibold text-dablue">
                {{insideService.priceService}}
              </div>

              <div class="text-center font-semibold text-dablue">
                НАЖМИТЕ, <br> ЧТОБЫ УЗНАТЬ БОЛЬШЕ
              </div>
            </div>
          </div>


          <transition>
            <div v-if="isClickServiceId.indexOf(insideService.id) != -1" class="flex flex-col gap-[23px] mt-[23px]">
              <TextBlock
                v-for="text in insideService.texts" :key="text"
                :text="text"
              />

              <div @click="isOpenServiceCharactersId.indexOf(insideService.id) != -1 ? isOpenServiceCharactersId.splice(isOpenServiceCharactersId.indexOf(insideService.id), 1) : isOpenServiceCharactersId.push(insideService.id)"  class="border-dapink border rounded-[29px] p-[2%]">
                <div class="flex flex-col gap-[13px] bg-lipink rounded-[24px] px-[5%] py-[4%] ">
                  <div class=" text-center text-white">
                    ПОСМОТРЕТЬ ПЕРСОНАЖЕЙ ДЛЯ ЭТОЙ УСЛУГИ
                  </div>
                </div>
              </div>

              <transition name="open-characters">
                <div v-if="isOpenServiceCharactersId.indexOf(insideService.id) != -1" class="flex flex-col gap-[23px]">
                  <div v-for="character in insideService.characters" :key="character">
                      <div class="border-dapink border rounded-[40px] p-[4%]">
                          <div>
                            <img :src="character.img" alt="" class="rounded-4xl w-full">
                          </div>
                      </div>

                      <div class="text-[20px] font-semibold mt-2">
                          {{character.title}}
                      </div>
                  </div>
                </div>
              </transition>

              <orderBlock />
            </div>
          </transition>
        </div>

        <orderBlock />
      </div>
    </transition>

    <transition name="open-characters">
      <div v-if="isClickOnDolls && isClickMenu == 'ПЕРСОНАЖИ'" class="flex flex-col gap-[23px]">
        <div v-for="character in service.characters" :key="character">
          <div @click="isClickCharactersId.indexOf(character.id) != -1 ? isClickCharactersId.splice(isClickCharactersId.indexOf(character.id), 1) : isClickCharactersId.push(character.id)">
            <div class=" border rounded-[40px] p-[4%]" :class="isClickCharactersId.indexOf(character.id) != -1 ? 'border-dablue' : 'border-dapink'">
                <div class="rounded-4xl" :class="isClickCharactersId.indexOf(character.id) != -1 ? 'bg-[#A0C6EA]' : 'bg-[#FCC6D4]'">
                  <img :src="character.gen_img" alt="" class="rounded-4xl w-full">
                  <div class="text-center text-[12px] p-[3%]">
                    УЗНАТЬ ПОДРОБНЕЕ
                  </div>
                </div>
            </div>

            <div class="text-[20px] font-semibold mt-2">
                {{character.title}}
            </div>
          </div>

          <transition name="open-characters">
            <div v-if="isClickCharactersId.indexOf(character.id) != -1" class="mt-8 flex flex-col gap-[23px]">
              <div v-for="img in character.imgs" :key="img" class="border-dapink border rounded-[40px] p-[4%]">
                  <div class="rounded-4xl">
                    <img :src="img" alt="" class="rounded-4xl w-full">
                  </div>
              </div>

              <div @click="isOpenCharacterServicesId.indexOf(character.id) != -1 ? isOpenCharacterServicesId.splice(isOpenCharacterServicesId.indexOf(character.id), 1) : isOpenCharacterServicesId.push(character.id)"  class="border-dapink border rounded-[29px] p-[2%]">
                <div class="bg-lipink rounded-[24px] px-[5%] py-[4%] ">
                  <div class=" text-center text-white">
                    ПОСМОТРЕТЬ УСЛУГИ С ЭТИМ ПЕРСОНАЖЕМ
                  </div>
                </div>
              </div>

              <transition>
                <div v-if="isOpenCharacterServicesId.indexOf(character.id) != -1" class="text-[14px] flex flex-col gap-[23px]">
                  <div v-for="characterService in character.services" :key="characterService">
                    <div  @click="isOpenCharacterInsideServicesId.indexOf(characterService.id) != -1 ? isOpenCharacterInsideServicesId.splice(isOpenCharacterInsideServicesId.indexOf(characterService.id), 1) : isOpenCharacterInsideServicesId.push(characterService.id)" class="border-dapink border rounded-[40px] p-[3.5%]">
                      <div class="flex flex-col gap-[13px] bg-liliblue rounded-4xl px-[8.5%] py-[5%] ">
                        <div class="text-[17px] font-semibold text-center">
                          {{characterService.titleService}}
                        </div>

                        <div class="text-center">
                          {{characterService.timeService}}
                        </div>

                        <div class="border-dablue border rounded-full px-[4.5%] py-[3%] text-center font-semibold text-dablue">
                          {{characterService.priceService}}
                        </div>

                        <div class="text-center font-semibold text-dablue">
                          НАЖМИТЕ, <br> ЧТОБЫ УЗНАТЬ БОЛЬШЕ
                        </div>
                      </div>
                    </div>

                    <transition>
                      <div v-if="isOpenCharacterInsideServicesId.indexOf(characterService.id) != -1" class="flex flex-col gap-[23px] mt-[23px]">
                        <TextBlock
                          v-for="text in characterService.texts" :key="text"
                          :text="text"
                        />
                      </div>
                    </transition>
                  </div>
                </div>
              </transition>
              
              <orderBlock v-if="character.id != Object.values(service.characters).pop().id" />
            </div>
          </transition>

        </div>

        <orderBlock  />
      </div>
    </transition>
</template>

<script setup>
import { ref, toRefs } from 'vue';

import orderBlock from '@/components/structure/orderBlock.vue';
import TextBlock from '@/components/structure/textBlock.vue';
// import blurPhoto from './blurPhoto.vue';

const props = defineProps(['service'])
const {service} = toRefs(props)

let isClickOnDolls = ref(false)
let isClickOnBlur = ref(false)
let isClickOnArrow = ref(false)

let isClickMenu = ref(false)
let isClickServiceId = ref([])
let isClickCharactersId = ref([])


let isOpenServiceCharactersId = ref([])
let isOpenCharacterServicesId = ref([])
let isOpenCharacterInsideServicesId = ref([])



function swimBlur() {
  if (!isClickOnBlur.value) {
    if (isClickOnArrow.value && isClickOnDolls.value) {
      isClickOnDolls.value = false
    } else {
      isClickOnDolls.value = true
    }
  } else {
    isClickOnDolls.value = false
  }
  isClickOnArrow.value = false
  isClickOnBlur.value = false

}
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
