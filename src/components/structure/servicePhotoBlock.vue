<template>
    <div>
        <div class="border-dapink border rounded-[40px] p-[4%]">
            <div>
            <img :src="img" alt="" class="rounded-4xl w-full">
            </div>
        </div>

        <div class="text-[20px] font-semibold mt-2">
            {{text}}
        </div>
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps(['img', 'text'])

const {img, text} = toRefs(props)
</script>