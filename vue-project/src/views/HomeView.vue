<template>
  <div>
    <PersonCard
      v-for="person in peopleForHire"
      :key="person.name"
      :Person="person"
    />
  </div>
</template>

<script setup>
import PersonCard from "@/components/PersonCard.vue";
const app = Vue.createApp({
  data(){
    return{
      symbols: ['🍒', '🍊', '🔔', '🍉', '🍋' ],
      reels: ['🍒', '🍊', '🔔'],
      spinning: false
    };
  },
  methods: {
    spin(){
      if (!this.spinning) {
        this.spinning = true;
        const getRandomSymbol = ()=>{
          return this.symbols[Math.floor(Math.random()*this.symbols.length)];
        }
        const spinReels = ()=> {
          for(let i=0; i<this.reels.length; i++){
            setTimeout(()=>{
              this.reels.splice(i, 1, getRandomSymbol());
            },
            i*200);
          }
          setTimeout(()=> {
            this.spinning = false;
          },
          this.reels.length * 200);
        };
        spinReels();
        }
      }
    }
  }
);
</script>



