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


// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyBaKxxKiw1wPY_n72rJZf8svE5oYJx76uA",
  authDomain: "fir-testing-123-365f7.firebaseapp.com",
  projectId: "fir-testing-123-365f7",
  storageBucket: "fir-testing-123-365f7.appspot.com",
  messagingSenderId: "221500252480",
  appId: "1:221500252480:web:7af9af338be26649d01aa5",
  measurementId: "G-KMWRGGP326"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
</script>



