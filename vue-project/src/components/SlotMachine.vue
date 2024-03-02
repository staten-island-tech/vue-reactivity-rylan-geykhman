<script setup>
import { ref, reactive } from 'vue';

const symbols = ['🍒', '🍊', '🍋', '🍇', '🍉'];
const reels = reactive(['➖', '➖', '➖']);
const spinning = ref(false);

function getRandomSymbol(){
  return symbols[Math.floor(Math.random() * symbols.length)];
};

function determineOutcome(){
  const [symbol1, symbol2, symbol3] = reels;
  if(symbol1 === symbol2 && symbol2 === symbol3){
    let outcome = "win";
    console.log(outcome);
  } else if(symbol1 === symbol2 || symbol2 === symbol3 || symbol1 === symbol3){
    let outcome = "partial-win";
    console.log(outcome);
  } else {
    let outcome = "lose";
    console.log(outcome);
  }
}

function spinReels(){
  for (let i = 0; i < reels.length; i++) {
    setTimeout(() => {
      reels[i] = getRandomSymbol();
    }, i * 500);
  }
  setTimeout(() => {
    determineOutcome();
    spinning.value = false;
  }, reels.length * 500);
};

function spin(){
  if (!spinning.value) {
    spinning.value = true;
    spinReels();
    handleSpinOutcome();
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