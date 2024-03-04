<script setup>
import {balance} from '@/somethings'
console.log(balance.balance)
</script>

<template>
  <div class="money">Balance: {{ balance.balance }}</div>
  <div class="money"v-if="balance.balance < 10" >Not enough money! Refresh to restart. (clicking spin button will just disable it :D)</div>
  <div v-else></div>
</template>

<style scoped>
.money {
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size:20px;
  color: #979191;
}
</style>

