<template>
    <div @click="isOpenCong = !isOpenCong" class="border-dapink border rounded-[40px] p-[3.5%]">
        <div class="flex flex-col gap-[13px] bg-liliblue rounded-4xl px-[8.5%] py-[5%] ">
          <div class="text-[17px] font-semibold text-center">
            {{title}}
          </div>

          <div class="text-center">
            {{time}}
          </div>

          <div class="border-dablue border rounded-full px-[4.5%] py-[3%] text-center font-semibold text-dablue">
            {{price}}
          </div>

          <div class="text-center font-semibold text-dablue">
            НАЖМИТЕ, <br> ЧТОБЫ УЗНАТЬ БОЛЬШЕ
          </div>
        </div>
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps(['title', 'time', 'price'])
const {title, time, price} = toRefs(props)
</script>