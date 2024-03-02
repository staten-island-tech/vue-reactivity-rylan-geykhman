<style>
  
</style>

<template>
  <div>
    <h1>Slots Simulation</h1>
    <SlotMachine :outcome="outcome"/>
    <Money :balance="balance" />
  </div>
</template>

<script>
import SlotMachine from '@/components/SlotMachine.vue';
import Money from '@/components/Money.vue';
  export default {
    components: { SlotMachine, Money },
    data() {
      return {
        outcome: ''
      }
    }
  }
</script>



