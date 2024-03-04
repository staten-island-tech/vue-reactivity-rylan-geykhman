<style>
h1, h3{
  text-align: center;
  color: #979191;
}
.body{
  height: 100vh;
  width: 100%;
  background: #1a2b45;
}
</style>

<template>
  <div class="body">
    <h1>Slots Simulation</h1>
    <SlotMachine @spin-complete="(outcome)=>console.log(outcome)"/>
    <Money :balance="balance" />
    <h3>Two of same symbol: +15$</h3>
    <h3>Three of same symbol: +50$</h3>
    <h3>Three different symbols: -10$</h3>
  </div>
</template>

<script>
import SlotMachine from '@/components/SlotMachine.vue';
import Money from '@/components/Money.vue';
import { balance } from '@/somethings'
console.log(balance.balance)
  export default {
    components: { SlotMachine, Money }
  }

</script>



