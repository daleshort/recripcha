<script setup></script>

<template>
  <img :src="`./assets/afgreeter.jpeg`" draggable="false" />
</template>

<style scoped>
img {
  animation-name: flashImage;
  animation-duration: .75s;
  animation-iteration-count: infinite;
}

@keyframes flashImage {
  from {
    -webkit-filter: grayscale(100%);
  }
  to {
    -webkit-filter: grayscale(0%);
  }
}
</style>
