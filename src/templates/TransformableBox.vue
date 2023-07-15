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

/**
 * hsvをrgbに変換する
 * hsvとrgbの値は0~255の整数
 */
function hsvToRgb(h: number, s: number, v: number): [r: number, g: number, b: number] {
  let r = v
  let g = v
  let b = v
  if (s <= 0) return [r, g, b]
  let _h = h * 6
  let i = Math.round((h * 6) / 255)
  let f = h - i * 255
  switch (i) {
    case 0:
      g *= 255 - s * (255 - f)
      b += 255 - s
      break
    case 1:
      r *= 255 - s * f
      b += 255 - s
      break
    case 2:
      b *= 255 - s * (255 - f)
      r += 255 - s
      break
    case 3:
      g *= 255 - s * f
      r += 255 - s
      break
    case 4:
      r *= 255 - s * (255 - f)
      g += 255 - s
      break
    case 5:
    default:
      b *= 255 - s * f
      g += 255 - s
      break
  }
  return [r, g, b]
}

function generateStyle() {
  let style = `left: ${props.posX}; top: ${props.posY};`
  // let r: number, g: number, b: number
  // ;[r, g, b] = hsvToRgb(props.colorH, props.colorS, props.colorV)
  // style += `background-color: #${r.toString(16)}${g.toString(16)}${b.toString(16)}`
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
