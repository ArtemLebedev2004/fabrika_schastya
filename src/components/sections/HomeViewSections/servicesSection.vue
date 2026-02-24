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

        <div v-for="service in servicesArr" :key="service.id" >
            <div @click="(event) => swimBlur(service.id, event)">
              <div class="relative ">
                <svg viewBox="0 0 337 198" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M276.052 0C275.935 0.331255 275.821 0.664375 275.714 1H42C19.3563 1 1 19.3563 1 42V156C1 178.644 19.3563 197 42 197H295C317.644 197 336 178.644 336 156V42C336 40.3718 335.901 38.7662 335.717 37.1875C336.018 36.8796 336.316 36.5676 336.606 36.249C336.864 38.1294 337 40.0489 337 42V156C337 178.834 318.779 197.411 296.084 197.986L295 198H42C19.1665 198 0.588625 179.779 0.0136719 157.084L0 156V42C0 18.804 18.804 3.2213e-08 42 0H276.052Z"
                    :fill="isClickOnTypeService.indexOf(service.id) != -1 ? '#397BD8' : '#C9185C'"/>
                </svg>

                <div class="absolute inset-x-[4%] inset-y-[6.5%]">
                    <img :src="service.serveTypePhoto" alt="" class="w-full h-full rounded-4xl min-[415px]:rounded-[36px]">

                    <transition>
                        <div v-if="isClickOnTypeService.indexOf(service.id) != -1" class="absolute -inset-[0.5%] ">
                            <svg width="100%" height="100%" viewBox="0 0 311 172" fill="none" xmlns="http://www.w3.org/2000/svg">
                              <foreignObject x="-11" y="-11" width="333" height="194"><div xmlns="http://www.w3.org/1999/xhtml" style="backdrop-filter:blur(5.5px);clip-path:url(#bgblur_0_1361_57_clip_path);height:100%;width:100%"></div></foreignObject><path data-figma-bg-blur-radius="11" d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z" fill="#FFD4DF" fill-opacity="0.69"/>
                              <defs>
                              <clipPath id="bgblur_0_1361_57_clip_path" transform="translate(11 11)"><path d="M261.015 0C261.544 19.4198 277.452 35 297 35C301.966 35 306.696 33.9941 311 32.1758V140C311 157.673 296.673 172 279 172H32C14.3269 172 0 157.673 0 140V32C2.70606e-06 14.3269 14.3269 0 32 0H261.015Z"/>
                              </clipPath></defs>
                            </svg>

                            <div ref="menuBlock" class="absolute w-[55%] h-[65%] m-auto inset-0 text-center text-dablue text-[17px] font-semibold flex flex-col justify-between items-center">
                              <div v-for="menuText in service.menuTexts" :key="menuText" @click="changeMenuTypeService(service.id, menuText)" class="relative">
                                <div class="relative z-1">
                                  {{ menuText }}
                                </div>

                                <div v-if="isClickMenuId.indexOf(service.id + menuText) != -1" class="absolute -inset-x-1 top-[50%] bottom-0 bg-pink-line-text rounded-full z-0">

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
                    :stroke="isClickOnTypeService.indexOf(service.id) != -1 ? '#397BD8' : '#C9185C'"/>
                    </svg>

                    <div class="absolute inset-[15%] rounded-full flex items-center p-[16%]" :class="isClickOnTypeService.indexOf(service.id) != -1 ? 'bg-liblue' : 'bg-lipink'">
                    <!-- <img src="/src/assets/icons/circle_main_photo.svg" alt="" class=" w-full"> -->
                    <img src="/src/assets/icons/arrow_right.svg" alt="" class="block w-full transition-all duration-150" :class="isClickOnTypeService.indexOf(service.id) != -1 ? ' rotate-180' : ''">
                    </div>
                </div>
              </div>

              <div class="text-[20px] font-semibold mt-2">
                {{service.titleTypeService}}
              </div>
            </div>


            <transition>
              <div v-if="isClickOnTypeService.indexOf(service.id) != -1 && isClickMenuId.indexOf(service.id + 'УСЛУГИ') != -1" class="text-[14px] flex flex-col gap-[23px] mt-8">
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

                      <orderBlock v-if="insideService.id != Object.values(service.services).pop().id"/>
                    </div>
                  </transition>
                </div>

                <orderBlock />
              </div>
            </transition>


            <transition name="open-characters">
              <div v-if="isClickOnTypeService.indexOf(service.id) != -1 && isClickMenuId.indexOf(service.id + 'ПЕРСОНАЖИ') != -1" class="flex flex-col gap-[23px] mt-8">
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

            <orderBlock
              v-if="isClickOnTypeService.indexOf(service.id) != -1 && isClickMenuId.indexOf(service.id + 'ЗАКАЗАТЬ') != -1"
              :withoutButton=true
            />
        </div>



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
import { ref, useTemplateRef } from 'vue';

// import ExpressCong from '../ServicesSection/ExpressCong.vue';
import TextBlockSmall from '@/components/structure/textBlockSmall.vue';
import orderBlock from '@/components/structure/orderBlock.vue';
import TextBlock from '@/components/structure/textBlock.vue';
//import typeServiceBlock from '../ServicesSection/typeServiceBlock.vue';

// let isClickOnDolls = ref(false)
let isOpenGallery = ref(false)
// let isOpenDolls = ref(false)

let isClickOnTypeService = ref([])
let menuBlock = useTemplateRef('menuBlock')
let isClickOnArrow = ref([])

let isClickMenuId = ref([])
let isClickServiceId = ref([])
let isClickCharactersId = ref([])


let isOpenServiceCharactersId = ref([])
let isOpenCharacterServicesId = ref([])
let isOpenCharacterInsideServicesId = ref([])

function swimBlur(serviceId, event) {
  if (isClickOnTypeService.value.indexOf(serviceId) == -1) {
    isClickOnTypeService.value.push(serviceId)
  } else if (menuBlock.value.indexOf(event.target.parentElement.parentElement) == -1) {
    isClickOnTypeService.value.splice(isClickOnTypeService.value.indexOf(serviceId), 1)
  }

  // console.log(isClickOnMenu)
  // if (isClickMenuId.value.indexOf(serviceId) == -1) {
  //   if (isClickOnArrow.value.indexOf(serviceId) != -1 && isClickOnTypeService.value.indexOf(serviceId) != -1) {
  //     isClickOnTypeService.value.splice(isClickOnTypeService.value.indexOf(serviceId), 1)
  //     isClickOnMenu.value.splice(isClickOnMenu.value.indexOf(serviceId), 1)
  //   } else if (isClickOnTypeService.value.indexOf(serviceId) == -1) {
  //     console.log('asdasd')
  //     isClickOnTypeService.value.push(serviceId)
  //   }
  // } else {
  //   isClickOnTypeService.value.splice(isClickOnTypeService.value.indexOf(serviceId), 1)
  //   isClickOnMenu.value.splice(isClickOnMenu.value.indexOf(serviceId), 1)

  // }
  // isClickOnArrow.value.splice(isClickOnArrow.value.indexOf(serviceId), 1)
}

function changeMenuTypeService(serviceId, menuText) {

  // console.log(isClickMenuId.value.includes([serviceId, menuText]))

    if (isClickMenuId.value.indexOf(serviceId + menuText) == -1) {

      for (let index = 0; index < isClickMenuId.value.length; index++) {

        if (isClickMenuId.value[index].indexOf(serviceId) != -1) {
          isClickMenuId.value.splice(index, 1)
          break
        }
      }
      isClickMenuId.value.push(serviceId + menuText)

      // console.log(isClickMenuId.value.indexOf([serviceId, menuText]))
    }
  // if (isClickMenuId.value.includes([serviceId, menuText]) == -1) {

  //   console.log(isClickMenuId.value)
  // }

}

eventBus.on('openGallery', (data) => {            // from gallerySection
  isOpenGallery.value = data
})

document.body.scrollTop = 0

let servicesArr = [

  {
    id: 'dolls',
    titleTypeService: 'РОСТОВЫЕ КУКЛЫ',
    serveTypePhoto: '/src/assets/img/serv_photo1.png',
    menuTexts: {
      menuText1: 'УСЛУГИ',
      menuText2: 'ПЕРСОНАЖИ',
      menuText3: 'ЗАКАЗАТЬ',
    },
    services: {
      congratulations: {
        id: 'dolls_service_1',
        titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
        timeService: '(10-30 минут)',
        priceService: '2600/3200 РУБ + ТАКСИ',
        texts: {
          text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
          text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
        },
        characters: {
          dandelion: {
            img: '/src/assets/img/big_dolls/dandelion/sm/dandelion_sm.jpg',
            title: 'ЗАЙЧИК-ОДУВАНЧИК'
          },
          marshmallow: {
            img: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows_sm.jpg',
            title: 'ЗАЙКА-ЗЕФИРКА'
          },
          snowflake: {
            img: '/src/assets/img/big_dolls/snowflake/sm/snowflake_sm.jpg',
            title: 'ЗАЙКА-СНЕЖИНКА'
          },
          zephyr: {
            img: '/src/assets/img/big_dolls/zephyr/sm/zephyr_sm.jpg',
            title: 'ЗЕФИР-ЗАЙЦЕВИЧ'
          },
          pupsBoy: {
            img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
            title: 'ПУПС МАЛЬЧИК - МИРОН'
          },
          pupsGirl: {
            img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
            title: 'ПУПС ДЕВОЧКА - ЕВА'
          },
          lolDoll: {
            img: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol_sm.jpg',
            title: 'КУКЛА ЛОЛ'
          },
          minion: {
            img: '/src/assets/img/big_dolls/minion/sm/minion_sm.jpg',
            title: 'МИНЬОН'
          },
        }
      },

      welcome: {
        id: 'dolls_service_2',
        titleService: 'WELCOME-ЗОНА',
        timeService: '(45-60 минут)',
        priceService: '3900 РУБ + ТАКСИ',
        texts: {
          text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
        },
        characters: {
          dandelion: {
            img: '/src/assets/img/big_dolls/dandelion/sm/dandelion_sm.jpg',
            title: 'ЗАЙЧИК-ОДУВАНЧИК'
          },
          marshmallow: {
            img: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows_sm.jpg',
            title: 'ЗАЙКА-ЗЕФИРКА'
          },
          snowflake: {
            img: '/src/assets/img/big_dolls/snowflake/sm/snowflake_sm.jpg',
            title: 'ЗАЙКА-СНЕЖИНКА'
          },
          zephyr: {
            img: '/src/assets/img/big_dolls/zephyr/sm/zephyr_sm.jpg',
            title: 'ЗЕФИР-ЗАЙЦЕВИЧ'
          },
          pupsBoy: {
            img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
            title: 'ПУПС МАЛЬЧИК - МИРОН'
          },
          pupsGirl: {
            img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
            title: 'ПУПС ДЕВОЧКА - ЕВА'
          },
          lolDoll: {
            img: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol_sm.jpg',
            title: 'КУКЛА ЛОЛ'
          },
          minion: {
            img: '/src/assets/img/big_dolls/minion/sm/minion_sm.jpg',
            title: 'МИНЬОН'
          }
        }
      },

      wedding: {
        id: 'dolls_service_3',
        titleService: 'ПРОГРАММА НА СВАДЬБУ ИЛИ НА ГЕНДЕР-ПАТИ',
        timeService: '(60 минут)',
        priceService: '4700 РУБ + ТАКСИ',
        texts: {
          text1: 'На пике популярности – шоу Ростовых кукол – Пупсов! Вы можете заказать это яркое развлечение на свадьбу или гендер пати',
          text2: 'На свадьбе наши Пупсы создадут незабываемую атмосферу, участвуя в захватывающем соревновании, где выяснится, кто же станет первым ребенком у молодоженов (даже если невеста не беременна)!',
          text3: 'А на гендер пати наши милые куклы раскроют сладкую тайну – кто же ждёт появления у мамы! Это не только весело, но и по-настоящему трогательно'
        },
        characters: {
          pupsBoy: {
            img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
            title: 'ПУПС МАЛЬЧИК - МИРОН'
          },
          pupsGirl: {
            img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
            title: 'ПУПС ДЕВОЧКА - ЕВА'
          }
        }
      },

      childs: {
        id: 'dolls_service_4',
        titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
        timeService: '(60 минут)',
        priceService: '4500 РУБ + ТАКСИ',
        texts: {
          text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
          text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
        },
        characters: {
          dandelion: {
            img: '/src/assets/img/big_dolls/dandelion/sm/dandelion_sm.jpg',
            title: 'ЗАЙЧИК-ОДУВАНЧИК'
          },
          marshmallow: {
            img: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows_sm.jpg',
            title: 'ЗАЙКА-ЗЕФИРКА'
          },
          snowflake: {
            img: '/src/assets/img/big_dolls/snowflake/sm/snowflake_sm.jpg',
            title: 'ЗАЙКА-СНЕЖИНКА'
          },
          zephyr: {
            img: '/src/assets/img/big_dolls/zephyr/sm/zephyr_sm.jpg',
            title: 'ЗЕФИР-ЗАЙЦЕВИЧ'
          },
          pupsBoy: {
            img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
            title: 'ПУПС МАЛЬЧИК - МИРОН'
          },
          pupsGirl: {
            img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
            title: 'ПУПС ДЕВОЧКА - ЕВА'
          }
        }
      },
    },
    characters: {
        dandelion: {
          id: 'dolls_character_1',
          gen_img: '/src/assets/img/big_dolls/dandelion/sm/dandelion_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/dandelion/sm/dandelion1_sm.jpg',
            img2: '/src/assets/img/big_dolls/dandelion/sm/dandelion2_sm.jpg',
          },
          title: 'ЗАЙЧИК-ОДУВАНЧИК',
          services: {
            congratulations: {
              id: 'dolls_dandelion_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_dandelion_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_character_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        marshmallows: {
          id: 'dolls_character_2',
          gen_img: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows1_sm.jpg',
            img2: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows2_sm.jpg',
            img3: '/src/assets/img/big_dolls/marshmallows/sm/marshmallows3_sm.jpg',
          },
          title: 'ЗАЙКА-ЗЕФИРКА',
          services: {
            congratulations: {
              id: 'dolls_marshmallows_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_marshmallows_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_marshmallows_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        snowflake: {
          id: 'dolls_character_3',
          gen_img: '/src/assets/img/big_dolls/snowflake/sm/snowflake_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/snowflake/sm/snowflake1_sm.jpg',
            img2: '/src/assets/img/big_dolls/snowflake/sm/snowflake2_sm.jpg',
            img3: '/src/assets/img/big_dolls/snowflake/sm/snowflake3_sm.jpg',
          },
          title: 'ЗАЙКА-СНЕЖИНКА',
          services: {
            congratulations: {
              id: 'dolls_snowflake_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_snowflake_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_snowflake_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        zephyr: {
          id: 'dolls_character_4',
          gen_img: '/src/assets/img/big_dolls/zephyr/sm/zephyr_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/zephyr/sm/zephyr1_sm.jpg',
            img2: '/src/assets/img/big_dolls/zephyr/sm/zephyr2_sm.jpg',
            img3: '/src/assets/img/big_dolls/zephyr/sm/zephyr3_sm.jpg',
          },
          title: 'ЗЕФИР-ЗАЙЦЕВИЧ',
          services: {
            congratulations: {
              id: 'dolls_zephyr_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_zephyr_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_zephyr_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        pupsBoy: {
          id: 'dolls_character_5',
          gen_img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy1_sm.jpg',
            img2: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy2_sm.jpg',
            img3: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy3_sm.jpg',
          },
          title: 'ПУПС МАЛЬЧИК - МИРОН',
          services: {
            wedding: {
              id: 'dolls_pups_boy_service_1',
              titleService: 'ПРОГРАММА НА СВАДЬБУ ИЛИ НА ГЕНДЕР-ПАТИ',
              timeService: '(60 минут)',
              priceService: '4700 РУБ + ТАКСИ',
              texts: {
                text1: 'На пике популярности – шоу Ростовых кукол – Пупсов! Вы можете заказать это яркое развлечение на свадьбу или гендер пати',
                text2: 'На свадьбе наши Пупсы создадут незабываемую атмосферу, участвуя в захватывающем соревновании, где выяснится, кто же станет первым ребенком у молодоженов (даже если невеста не беременна)!',
                text3: 'А на гендер пати наши милые куклы раскроют сладкую тайну – кто же ждёт появления у мамы! Это не только весело, но и по-настоящему трогательно'
              }
            }
          }
        },

        pupsGirl: {
          id: 'dolls_character_6',
          gen_img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl1_sm.jpg',
            img2: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl2_sm.jpg',
          },
          title: 'ПУПС ДЕВОЧКА - ЕВА',
          services: {
            wedding: {
              id: 'dolls_pups_girl_service_1',
              titleService: 'ПРОГРАММА НА СВАДЬБУ ИЛИ НА ГЕНДЕР-ПАТИ',
              timeService: '(60 минут)',
              priceService: '4700 РУБ + ТАКСИ',
              texts: {
                text1: 'На пике популярности – шоу Ростовых кукол – Пупсов! Вы можете заказать это яркое развлечение на свадьбу или гендер пати',
                text2: 'На свадьбе наши Пупсы создадут незабываемую атмосферу, участвуя в захватывающем соревновании, где выяснится, кто же станет первым ребенком у молодоженов (даже если невеста не беременна)!',
                text3: 'А на гендер пати наши милые куклы раскроют сладкую тайну – кто же ждёт появления у мамы! Это не только весело, но и по-настоящему трогательно'
              }
            }
          }
        },

        doll_lol: {
          id: 'dolls_character_7',
          gen_img: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol1_sm.jpg',
            img2: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol2_sm.jpg',
          },
          title: 'КУКЛА ЛОЛ',
          services: {
            congratulations: {
              id: 'dolls_doll_lol_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_doll_lol_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },
          }
        },
        minion: {
          id: 'dolls_character_8',
          gen_img: '/src/assets/img/big_dolls/minion/sm/minion_sm.jpg',
          imgs: {},
          title: 'МИНЬОН',
          services: {
            congratulations: {
              id: 'dolls_minion_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_minion_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },
          }
        }
      }
  },


  {
    id: 'animators',
    titleTypeService: 'АНИМАЦИОННЫЕ ПЕРСОНАЖИ',
    serveTypePhoto: '/src/assets/img/serv_photo2.png',
    menuTexts: {
      menuText1: 'УСЛУГИ',
      menuText2: 'ПЕРСОНАЖИ',
      menuText3: 'ЗАКАЗАТЬ',
    },
    services: {
      postcard: {
        id: 'animators_service_1',
        titleService: 'ЖИВАЯ ОТКРЫТКА ИГРОВОГО ПЕРСОНАЖА',
        timeService: '(15 минут)',
        priceService: '2000 РУБ + ТАКСИ',
        texts: {
          text1: 'Это 15-минутное камерное поздравление от вашего любимого игрового героя. В отличие от шумных игровых программ, здесь акцент делается на тесном, трогательном взаимодействии. Именинник остается один на один со своим кумиром, получая возможность не только услышать поздравления, но и поговорить о своих мечтах и желаниях, поделиться успехами, узнать о талантах персонажа, а также насладиться небольшим танцем и игрой. Это нежное и личное поздравление, созданное для особенных моментов.',
        },
        characters: {
          trolli: {
            img: '/src/assets/img/animators/trolli/sm/trolli_sm.jpg',
            title: 'РОЗОЧКА ИЗ М/Ф «ТРОЛЛИ»'
          },
          unicorn: {
            img: '/src/assets/img/animators/unicorn/sm/unicorn_sm.jpg',
            title: 'ЕДИНОРОЖКА ИСКОРКА ИЗ «МАЙ ЛИТТЛ ПОНИ»'
          },
          sky: {
            img: '/src/assets/img/animators/sky/sm/sky_sm.jpg',
            title: 'СКАЙ ИЗ ЩЕНЯЧЬЕГО ПАТРУЛЯ'
          },
          marshal: {
            img: '/src/assets/img/animators/marshal/sm/marshal_sm.jpg',
            title: 'МАРШАЛ ИЗ ЩЕНЯЧЬЕГО ПАТРУЛЯ'
          },
          ice_cream: {
            img: '/src/assets/img/animators/ice_cream/sm/ice_cream_sm.jpg',
            title: 'АПЕЛЬСИНОВОЕ МОРОЖЕНОЕ'
          },
          spider: {
            img: '/src/assets/img/animators/spider/sm/spider_sm.jpg',
            title: 'ЧЕЛОВЕК-ПАУК'
          },
          cold_heart: {
            img: '/src/assets/img/animators/cold_heart/sm/cold_heart_sm.jpg',
            title: 'АННА ИЗ ХОЛОДНОГО СЕРДЦА'
          },
          snow_white: {
            img: '/src/assets/img/animators/snow_white/sm/snow_white_sm.jpg',
            title: 'БЕЛОСНЕЖКА'
          },
          pirate: {
            img: '/src/assets/img/animators/pirate/sm/pirate_sm.jpg',
            title: 'ПИРАТКА'
          },
          batman: {
            img: '/src/assets/img/animators/batman/sm/batman_sm.jpg',
            title: 'БЭТМЕН'
          },
          astronaut: {
            img: '/src/assets/img/animators/astronaut/sm/astronaut_sm.jpg',
            title: 'КОСМОНАВТ'
          },
          tiktok: {
            img: '/src/assets/img/animators/tiktok/sm/tiktok_sm.jpg',
            title: 'БЛОГЕР ИЗ ТИКТОКА'
          },
          gramm: {
            img: '/src/assets/img/animators/gramm/sm/gramm_sm.jpg',
            title: 'БЛОГЕР ИЗ ИНСТАГРАММА'
          }
        }
      },

      childs: {
        id: 'animators_service_2',
        titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
        timeService: '(30 минут)',
        priceService: 'ОТ 2600 РУБ + ТАКСИ',
        texts: {
          text1: 'Это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки',
        },
        characters: {
          trolli: {
            img: '/src/assets/img/animators/trolli/sm/trolli_sm.jpg',
            title: 'РОЗОЧКА ИЗ М/Ф «ТРОЛЛИ»'
          },
          unicorn: {
            img: '/src/assets/img/animators/unicorn/sm/unicorn_sm.jpg',
            title: 'ЕДИНОРОЖКА ИСКОРКА ИЗ «МАЙ ЛИТТЛ ПОНИ»'
          },
          sky: {
            img: '/src/assets/img/animators/sky/sm/sky_sm.jpg',
            title: 'СКАЙ ИЗ ЩЕНЯЧЬЕГО ПАТРУЛЯ'
          },
          marshal: {
            img: '/src/assets/img/animators/marshal/sm/marshal_sm.jpg',
            title: 'МАРШАЛ ИЗ ЩЕНЯЧЬЕГО ПАТРУЛЯ'
          },
          ice_cream: {
            img: '/src/assets/img/animators/ice_cream/sm/ice_cream_sm.jpg',
            title: 'АПЕЛЬСИНОВОЕ МОРОЖЕНОЕ'
          },
          spider: {
            img: '/src/assets/img/animators/spider/sm/spider_sm.jpg',
            title: 'ЧЕЛОВЕК-ПАУК'
          },
          cold_heart: {
            img: '/src/assets/img/animators/cold_heart/sm/cold_heart_sm.jpg',
            title: 'АННА ИЗ ХОЛОДНОГО СЕРДЦА'
          },
          snow_white: {
            img: '/src/assets/img/animators/snow_white/sm/snow_white_sm.jpg',
            title: 'БЕЛОСНЕЖКА'
          },
          pirate: {
            img: '/src/assets/img/animators/pirate/sm/pirate_sm.jpg',
            title: 'ПИРАТКА'
          },
          batman: {
            img: '/src/assets/img/animators/batman/sm/batman_sm.jpg',
            title: 'БЭТМЕН'
          },
          astronaut: {
            img: '/src/assets/img/animators/astronaut/sm/astronaut_sm.jpg',
            title: 'КОСМОНАВТ'
          },
          tiktok: {
            img: '/src/assets/img/animators/tiktok/sm/tiktok_sm.jpg',
            title: 'БЛОГЕР ИЗ ТИКТОКА'
          },
          gramm: {
            img: '/src/assets/img/animators/gramm/sm/gramm_sm.jpg',
            title: 'БЛОГЕР ИЗ ИНСТАГРАММА'
          }
        }
      }
    },
    characters: {
        trolli: {
          id: 'animators_character_1',
          gen_img: '/src/assets/img/animators/trolli/sm/trolli_sm.jpg',
          imgs: {
            img1: '/src/assets/img/animators/dandelion/sm/dandelion1_sm.jpg',
            img2: '/src/assets/img/animators/dandelion/sm/dandelion2_sm.jpg',
          },
          title: 'ЗАЙЧИК-ОДУВАНЧИК',
          services: {
            congratulations: {
              id: 'animators_dandelion_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_dandelion_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_character_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        marshmallows: {
          id: 'dolls_character_2',
          gen_img: '/src/assets/img/animators/marshmallows/sm/marshmallows_sm.jpg',
          imgs: {
            img1: '/src/assets/img/animators/marshmallows/sm/marshmallows1_sm.jpg',
            img2: '/src/assets/img/animators/marshmallows/sm/marshmallows2_sm.jpg',
            img3: '/src/assets/img/animators/marshmallows/sm/marshmallows3_sm.jpg',
          },
          title: 'ЗАЙКА-ЗЕФИРКА',
          services: {
            congratulations: {
              id: 'dolls_marshmallows_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_marshmallows_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_marshmallows_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        snowflake: {
          id: 'dolls_character_3',
          gen_img: '/src/assets/img/animators/snowflake/sm/snowflake_sm.jpg',
          imgs: {
            img1: '/src/assets/img/animators/snowflake/sm/snowflake1_sm.jpg',
            img2: '/src/assets/img/animators/snowflake/sm/snowflake2_sm.jpg',
            img3: '/src/assets/img/animators/snowflake/sm/snowflake3_sm.jpg',
          },
          title: 'ЗАЙКА-СНЕЖИНКА',
          services: {
            congratulations: {
              id: 'dolls_snowflake_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_snowflake_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_snowflake_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        zephyr: {
          id: 'dolls_character_4',
          gen_img: '/src/assets/img/animators/zephyr/sm/zephyr_sm.jpg',
          imgs: {
            img1: '/src/assets/img/animators/zephyr/sm/zephyr1_sm.jpg',
            img2: '/src/assets/img/animators/zephyr/sm/zephyr2_sm.jpg',
            img3: '/src/assets/img/animators/zephyr/sm/zephyr3_sm.jpg',
          },
          title: 'ЗЕФИР-ЗАЙЦЕВИЧ',
          services: {
            congratulations: {
              id: 'dolls_zephyr_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_zephyr_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },

            childs: {
              id: 'dolls_zephyr_service_3',
              titleService: 'ДЕТСКАЯ ИГРОВАЯ ПРОГРАММА',
              timeService: '(60 минут)',
              priceService: '4500 РУБ + ТАКСИ',
              texts: {
                text1: 'Детская игровая программа Ростовой куклы – это комплекс разнообразных активностей, которые помогают детям развлекаться и развивать свои навыки. Похожа на стандартную игровую программу анимационных персонажей, только с большой плюшевой игрушкой',
                text2: 'Игровая программа включает в себя активные игры и большое количество зажигательных танцев. Может проводиться как в помещении, так и на свежем воздухе. На программу едут два артиста, один в костюме, второй ассистент, что позволяет создать незабываемую, сказочную программу',
              }
            },
          }
        },

        pupsBoy: {
          id: 'dolls_character_5',
          gen_img: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy1_sm.jpg',
            img2: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy2_sm.jpg',
            img3: '/src/assets/img/big_dolls/pups_boy/sm/pups_boy3_sm.jpg',
          },
          title: 'ПУПС МАЛЬЧИК - МИРОН',
          services: {
            wedding: {
              id: 'dolls_pups_boy_service_1',
              titleService: 'ПРОГРАММА НА СВАДЬБУ ИЛИ НА ГЕНДЕР-ПАТИ',
              timeService: '(60 минут)',
              priceService: '4700 РУБ + ТАКСИ',
              texts: {
                text1: 'На пике популярности – шоу Ростовых кукол – Пупсов! Вы можете заказать это яркое развлечение на свадьбу или гендер пати',
                text2: 'На свадьбе наши Пупсы создадут незабываемую атмосферу, участвуя в захватывающем соревновании, где выяснится, кто же станет первым ребенком у молодоженов (даже если невеста не беременна)!',
                text3: 'А на гендер пати наши милые куклы раскроют сладкую тайну – кто же ждёт появления у мамы! Это не только весело, но и по-настоящему трогательно'
              }
            }
          }
        },

        pupsGirl: {
          id: 'dolls_character_6',
          gen_img: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl1_sm.jpg',
            img2: '/src/assets/img/big_dolls/pups_girl/sm/pups_girl2_sm.jpg',
          },
          title: 'ПУПС ДЕВОЧКА - ЕВА',
          services: {
            wedding: {
              id: 'dolls_pups_girl_service_1',
              titleService: 'ПРОГРАММА НА СВАДЬБУ ИЛИ НА ГЕНДЕР-ПАТИ',
              timeService: '(60 минут)',
              priceService: '4700 РУБ + ТАКСИ',
              texts: {
                text1: 'На пике популярности – шоу Ростовых кукол – Пупсов! Вы можете заказать это яркое развлечение на свадьбу или гендер пати',
                text2: 'На свадьбе наши Пупсы создадут незабываемую атмосферу, участвуя в захватывающем соревновании, где выяснится, кто же станет первым ребенком у молодоженов (даже если невеста не беременна)!',
                text3: 'А на гендер пати наши милые куклы раскроют сладкую тайну – кто же ждёт появления у мамы! Это не только весело, но и по-настоящему трогательно'
              }
            }
          }
        },

        doll_lol: {
          id: 'dolls_character_7',
          gen_img: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol_sm.jpg',
          imgs: {
            img1: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol1_sm.jpg',
            img2: '/src/assets/img/big_dolls/doll_lol/sm/doll_lol2_sm.jpg',
          },
          title: 'КУКЛА ЛОЛ',
          services: {
            congratulations: {
              id: 'dolls_doll_lol_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_doll_lol_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },
          }
        },
        minion: {
          id: 'dolls_character_8',
          gen_img: '/src/assets/img/big_dolls/minion/sm/minion_sm.jpg',
          imgs: {},
          title: 'МИНЬОН',
          services: {
            congratulations: {
              id: 'dolls_minion_service_1',
              titleService: 'ЭКСПРЕСС/СТАНДАРТ ПОЗДРАВЛЕНИЕ',
              timeService: '(10-30 минут)',
              priceService: '2600/3200 РУБ + ТАКСИ',
              texts: {
                text1: 'Поздравления Ростовых кукол - уникальное сочетание интерактивности и душевности, поскольку в отличие от других, наши персонажи умеют разговаривать, что позволяет создавать уникальные поздравления и вести живой диалог с каждым именинником и гостями, делая каждое представление по-настоящему уникальным',
                text2: 'Мы насыщаем праздник танцевальными блоками с музыкой, подобранной специально под ваши предпочтения, обеспечивая активное вовлечение всех гостей, и гарантируем большое количество ярких, запоминающихся фотографий благодаря активному взаимодействию кукол и созданию позитивных моментов, а также предлагаем торжественную церемонию вручения подарков через наших плюшевых гигантов, что добавляет особую радость и значимость моменту'
              }
            },

            welcome: {
              id: 'dolls_minion_service_2',
              titleService: 'WELCOME-ЗОНА',
              timeService: '(45-60 минут)',
              priceService: '3900 РУБ + ТАКСИ',
              texts: {
                text1: 'Наши ростовые куклы встречают гостей вашего мероприятия, фотографируются с ними, создают настроение предстоящего события',
              }
            },
          }
        }
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
