<script setup>
import { ref } from 'vue';

const balance = ref(100); 

const handleSpinComplete = (outcome) => {
  if (outcome === 'win') {
    balance.value += 50;
  } else if (outcome === 'partial-win') {
    balance.value += 15;
  } else {
    balance.value -= 10;
  }
};
</script>

<template>
  <div id="app">
    <SlotMachine @spin-complete="handleSpinComplete" />
    <Money :balance="balance" />
  </div>
</template>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>