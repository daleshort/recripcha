<script setup></script>

<template>
  <div class="welcome">
    <font-awesome-icon
      icon="fa-brands fa-accessible-icon"
      draggable="false"
      color="blue"
      transform="grow-300"
    />
  </div>

  <img :src="`./assets/deal-with-it.png`" draggable="false" />
</template>

<style scoped>
.welcome {
  margin-top: 160px;
}

img {
  width: 80px;
  position: relative;
  left: 80px;
  bottom: 175px;
  animation-name: moveGlasses;
  animation-duration: 2s;
}

@keyframes moveGlasses {
  from {
    bottom: 400px;
  }
  to {
    bottom: 175px;
  }
}
</style>
