<script setup>
import { ref } from "vue";

//make count not reactive
let count = 0;
const getCount = () => {
  //remove .value
  count += 1;
  return count;
};
</script>

<template>
  <ul>
    <li>{{ getCount() }}</li>
    <li>{{ getCount() }}</li>
    <li>{{ getCount() }}</li>
  </ul>
</template>
