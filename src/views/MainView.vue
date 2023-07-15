<script setup lang="ts">
import TransformableBox from '../templates/TransformableBox.vue'
import { ref } from 'vue'

let x = ref<number>(20)
let y = ref<number>(20)
let h = ref<number>(0)
let s = ref<number>(100)
let l = ref<number>(100)
</script>

<template>
  <div id="main">
    <TransformableBox :posX="x" :posY="y" :colorH="h" :colorS="s" :colorL="l" />
    <div class="input">
      <div class="x">
        <label>X:</label>
        <input type="number" v-model="x" min="0" max="5000" />
      </div>
      <div class="y">
        <label>Y:</label>
        <input type="number" v-model="y" min="0" max="5000" />
      </div>
      <div class="h">
        <label>H:</label>
        <input type="number" v-model="h" min="0" max="360" />
      </div>
      <div class="s">
        <label>S:</label>
        <input type="number" v-model="s" min="0" max="255" />
      </div>
      <div class="l">
        <label>L:</label>
        <input type="number" v-model="l" min="0" max="255" />
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
#main {
  width: 100%;
  height: 100%;
  background-color: #000;
}
.input {
  position: fixed;
  bottom: 0;
  display: flex;
  flex-direction: row;
  color: white;

  label {
    margin: 0 0.5em;
  }
}
</style>
