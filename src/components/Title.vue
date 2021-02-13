<!--Vanessa Gutierrez 02/12/2021-->
<template>
  <h1 class="text-6xl font-semibold text-pink-500 text-center">
    {{ msg }}
  </h1>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  msg: {
    type: String,
    default: 'Custom Title',
  },
})
</script>
