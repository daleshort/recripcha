<script setup>
import { ref } from "vue";
defineProps({
  statusText: String,
});
</script>

<template>
  <div class="mb-2 mt-2 tag is-size-6" :class="statusText=='Ableist Scum Detected'? 'is-danger' : 'is-info' ">
    {{ statusText }}
  </div>
</template>

<style scoped></style>
