<script setup lang="ts">
import { ref } from 'vue'
defineProps<{
  num: number
}>()
defineEmits<{
  (e: 'update:num', num: number): void
}>()

let num = ref<number>()
</script>

<template>
  <input type="number" :value="num" @input="$emit('update:num', num)" />
</template>
