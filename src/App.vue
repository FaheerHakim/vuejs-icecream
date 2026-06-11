<script setup>
import IcecreamOrder from'./components/icecreamOrder.vue'
import IcecreamConfig from'./components/IcecreamConfig.vue'
</script>

<template>
  <div class="app">
  <div class="kolom">
  <IcecreamOrder />

  </div>

  <div class="kolom configurator" >
  <IcecreamConfig />

  </div>
  </div>
</template>

<style scoped></style>
