<template>
  <div class="cards-wrapper">
    <Card class="deck" />
    <Card
      v-for="(card, i) in cards"
      :key="i"
      :flip="card.flipped"
    />
  </div>
  <button
    class="btn"
    @click="flipCard(1)"
    v-text="'Play'"
  />
</template>

<script setup lang="ts">
import { reactive } from "vue";
import Card from "@/components/Card.vue";

const cards = reactive([
  { id:1, flipped: false },
  { id:2, flipped: false },
  { id:3, flipped: false }
]);

function flipCard(index: number) {
  const card = cards[index]
  card.flipped = !card.flipped;
}

</script>

<style scoped>
.cards-wrapper {
  display: flex;
  position: relative;
}
.deck {
  position: absolute;
  left: 52%;
  transform: translateX(-50%) translateY(-105%);
}
</style>
