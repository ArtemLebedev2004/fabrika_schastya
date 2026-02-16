<template>
    <div class="p-4.25 border-dapink border rounded-[25px] mt-7 text-dablue text-[14px] text-center">
        {{ text }}
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps(['text'])
const {text} = toRefs(props)
</script>