<script setup>
import { ref } from 'vue';
import { outcome } from '@/views/HomeView.vue'

let balance = ref(100)
function handleSpinComplete(){
  if (outcome === 'win') {
    balance.value += 50;
    console.log(balance)
  } else if (outcome === 'partial-win') {
    balance.value += 15;
    console.log(balance)
  } else {
    balance.value -= 10;
    console.log(balance)
  }
}
</script>

<!-- @click=$emit('balanceChange',state) -->
<template>
  <div>{{ balance }}</div>
</template>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>

