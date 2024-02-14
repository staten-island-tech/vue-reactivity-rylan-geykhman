<script setup>
import PersonCard from "@/components/PersonCard.vue";
const peopleForHire = [
  {
    name: "Yan",
    codingProwess: 9,
    price: 25,
  },
  {
    name: "Gabe",
    codingProwess: 7,
    price: 20, 
  },
  {
    name: "Noah A.",
    codingProwess: 7.5,
    price: 22, 
  },
  {
    name: "Tristian",
    codingProwess: 4,
    price: 4,
  },
  {
    name: "Noah R.",
    codingProwess: 9,
    price: 25, 
  },
]
</script>

<template>
  <div>
    <PersonCard
      v-for="person in peopleForHire"
      :key="person.name"
      :Person="person"
    />
  </div>
</template>
