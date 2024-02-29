<script setup>
import { ref, reactive } from 'vue';

const symbols = ['🍒', '🍊', '🍋', '🍇', '🍉'];
const reels = reactive(['➖', '➖', '➖']);
const spinning = ref(false);

function getRandomSymbol(){
  return symbols[Math.floor(Math.random() * symbols.length)];
};

function spinReels(){
  for (let i = 0; i < reels.length; i++) {
    setTimeout(() => {
      reels[i] = getRandomSymbol();
    }, i * 200);
  }
  setTimeout(() => {
    spinning.value = false;
  }, reels.length * 200);
};

function spin(){
  if (!spinning.value) {
    spinning.value = true;
    spinReels();
  }
}
</script>

<template>
  <div id="app">
    <div class="reel" v-for="(symbol, index) in reels" :key="index">{{ symbol }}</div>
    <br>
    <button @click="spin" :disabled="spinning">Spin</button>
  </div>
</template>

<style scoped>
.reel {
    display: inline-block;
    width: 100px;
    height: 150px;
    border: 1px solid #ccc;
    margin: 0 10px;
    text-align: center;
    font-size: 24px;
  }
</style>