<template>
  <div
    class="card"
    :class="{flip: props.flip}"
  >
    <img src="@/assets/img/card/back.png" class="card-inner back" alt="back"/>
    <img src="@/assets/img/card/front.png" class="card-inner front" alt="front"/>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  flip: boolean;
}>();
</script>

<style scoped>
.card {
  width: 185px;
  height: 277px;
  margin: 40px 5px;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;

  @media (max-width: 630px) or (max-height: 880px) {
    width: 100px;
    height: 160px;
  }
  @media (max-width: 350px) or (max-height: 525px)  {
    width: 70px;
    height: 120px;
  }
}

.card-inner {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  border-radius: 10px;
}

.front {
  transform: rotateY(180deg);
}

.flip {
  animation: flip 1s ease-in-out forwards;
}

@keyframes flip {
  20% {
    transform:rotateY(180deg);
  }
  60% {
    transform:translateY(-110%) rotateY(180deg);
  }
  100% {
    transform:translateY(-110%) rotateY(180deg);
    position: absolute;
    left: 25%;
  }
}

</style>
