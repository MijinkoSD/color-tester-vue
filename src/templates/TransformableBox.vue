<script setup lang="ts">
import { onBeforeUpdate, ref } from 'vue'
let props = defineProps<{
  posX: number
  posY: number
  colorH: number
  colorS: number
  colorV: number
}>()

let styleValue = ref<string>('')

onBeforeUpdate(() => {
  generateStyle()
})

function generateStyle() {
  let style = `left: ${props.posX}; top: ${props.posY};`
  style += `background-color: hsl(${props.colorH}deg ${(props.colorS * 100) / 255}% ${
    (props.colorV * 100) / 255
  }%)`
  styleValue.value = style
}
</script>

<template>
  <div class="box" :style="styleValue"></div>
</template>

<style scoped lang="scss">
.box {
  position: absolute;
  display: block;
  width: 200px;
  height: 200px;
}
</style>
