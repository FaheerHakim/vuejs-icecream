<script setup>
import { ref } from 'vue'
import IcecreamOrder from'./components/icecreamOrder.vue'
import IcecreamConfig from'./components/icecreamConfig.vue'

const selectedFlavor = ref('')
const selectedConeFlavor = ref('')


</script>

<template>
  <div class="app">
  <div class="kolom">
  <IcecreamOrder 
  @flavorChanged="selectedFlavor = $event" 
  @coneFlavorChanged="selectedConeFlavor = $event" 
   />


  </div>

  <div class="kolom">
  <IcecreamConfig :flavor="selectedFlavor" :coneFlavor="selectedConeFlavor" />

  </div>
  </div>
</template>

<style scoped>
.kolom{

display: grid;
grid-template-columns: 8fr 4fr;

}
</style>
