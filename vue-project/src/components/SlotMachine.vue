<script setup>
import { ref, reactive } from 'vue';
import {balance} from '@/somethings';

const symbols = ['🍒', '🍊', '🍋', '🍇', '🍉', '💵', '🍎', '🎱', '🎰', '🎲'];
const reels = reactive(['➖', '➖', '➖']);
const spinning = ref(false);
const outcome = ref('')

function getRandomSymbol(){
  return symbols[Math.floor(Math.random() * symbols.length)];
};

function determineOutcome(){
  const [symbol1, symbol2, symbol3] = reels;
  if(symbol1 === symbol2 && symbol2 === symbol3){
    outcome.value = 'win';
  } else if(symbol1 === symbol2 || symbol2 === symbol3 || symbol1 === symbol3){
    outcome.value = 'partial-win';
  } else {
    outcome.value = 'lose';
  };
}

function spinReels(){
  if(balance.balance >= 10){
  for (let i = 0; i < reels.length; i++) {
    setTimeout(() => {
      reels[i] = getRandomSymbol();
    }, i * 500);
  }
  setTimeout(() => {
    determineOutcome();
    spinning.value = false;
    handleSpinComplete(outcome);
  }, reels.length * 500);
} else{
  console.log("not enough money! refresh to restart.")
}};

function handleSpinComplete(outcome){
  if (outcome.value === 'win') {
    balance.balance += 50;
  } else if (outcome.value === 'partial-win') {
    balance.balance += 15;
  } else {
    balance.balance -= 10;
  }
}

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
  <div id="outcome" v-if="outcome==='win'">Jackpot! +50$</div>
  <div id="outcome" v-else-if="outcome==='partial-win'">Two Same: +15$</div>
  <div id="outcome" v-else-if="outcome==='lose'">Three Different: -10$</div>
</template>

<style scoped>
.reel {
  display: flex;
  justify-content: center;
  align-items: center;
  background: #fafafa;
  width: 100px;
  height: 150px;
  border: 1px solid #000000;
  margin: 10px;
  font-size: 24px;
}
.reel div {
  display: flex;
  align-items: center;
  height: 100%;
}
#app {
  height: 25%;
  background: #1a2b45;
  display: flex;
  justify-content: center;
  align-items: center;
}
#outcome{
  padding: 10px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  font-size:20px;
  color: #979191;
}
</style>
