<style>
  
</style>

<template>
  <div>
    <h1>Slots Simulation</h1>
    <SlotMachine />
    <Money />
  </div>
</template>

<script>
import SlotMachine from '@/components/SlotMachine.vue';
import Money from '@/components/Money.vue'
let balance = ref(100); 
  export default {
    components: { SlotMachine, Money }
  }
</script>



