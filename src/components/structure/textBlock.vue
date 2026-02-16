<template>
    <div class="backdrop-blur-xs leading-6 border-dapink border rounded-[30px] py-[5%] px-[7%]">
        {{ text }}
    </div>
</template>

<script setup>
import { toRefs } from 'vue';

const props = defineProps([
    'text'
])

const { text } = toRefs(props)
</script>