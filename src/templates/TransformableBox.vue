<script setup lang="ts">
defineProps<{
  posX: number
  posY: number
  width?: number
  height?: number
  colorH: number
  colorS: number
  colorL: number
}>()
</script>

<template>
  <div
    class="box"
    :style="{
      left: posX + 'px',
      top: posY + 'px',
      width: width + 'px',
      height: height + 'px',
      backgroundColor: `hsl(${colorH}deg ${colorS}% ${colorL}%)`
    }"
  ></div>
</template>

<style scoped lang="scss">
.box {
  position: absolute;
  display: block;
  width: 200px;
  height: 200px;
}
</style>
