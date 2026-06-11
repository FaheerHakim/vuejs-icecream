<script setup>
import IcecreamOrder from'./components/icecreamOrder.vue'
import IcecreamConfig from'./components/icecreamConfig.vue'
</script>

<template>
  <div class="app">
  <div class="kolom">
  <IcecreamOrder />

  </div>

  <div class="kolom">
  <IcecreamConfig />

  </div>
  </div>
</template>

<style scoped>
.kolom{

display: grid;
grid-template-columns: 8fr 4fr;

}
</style>
