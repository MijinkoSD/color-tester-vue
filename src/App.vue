<script setup lang="ts">
import MainView from '@/views/MainView.vue'
</script>

<template id="app">
  <MainView />
</template>

<style lang="scss">
*,
*::after,
*::before {
  box-sizing: content-box;
}
body {
  margin: 0;
  padding: 0;
  height: 100%;
}
#app {
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 0;
}
</style>
