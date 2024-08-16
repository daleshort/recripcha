<script setup>
import { ref } from "vue";
import DotSquare from "./DotSquare.vue";

const emit = defineEmits(["submit"]);
const clickCount = ref(0);
var arr = [];
while (arr.length < 9) {
  var r = Math.floor(Math.random() * 9) + 1;
  if (arr.indexOf(String(r)) === -1) {
    arr.push(String(r));
  }
}

const handleSquareClick = ({ value }) => {
  
  if (value) {
    clickCount.value += 1;
  } else {
    clickCount.value -= 1;
  }

};
const handleSubmit = () => {
  if (clickCount.value == 0) {
    emit("submit", true);
  } else {
    emit("submit", false);
  }
};

console.log(arr);
</script>

<template>
  <div class="grid-container">
    <div class="row-container">
      <DotSquare
        :dotNumber="arr[0]"
        @squareClick="handleSquareClick"
      /><DotSquare
        :dotNumber="arr[1]"
        @squareClick="handleSquareClick"
      /><DotSquare :dotNumber="arr[2]" @squareClick="handleSquareClick" />
    </div>
    <div class="row-container">
      <DotSquare
        :dotNumber="arr[3]"
        @squareClick="handleSquareClick"
      /><DotSquare
        :dotNumber="arr[4]"
        @squareClick="handleSquareClick"
      /><DotSquare :dotNumber="arr[5]" @squareClick="handleSquareClick" />
    </div>
    <div class="row-container">
      <DotSquare
        :dotNumber="arr[6]"
        @squareClick="handleSquareClick"
      /><DotSquare
        :dotNumber="arr[7]"
        @squareClick="handleSquareClick"
      /><DotSquare :dotNumber="arr[8]" @squareClick="handleSquareClick" />
    </div>
  </div>
  <div class="mt-2 mb-2">Select all pseudoisochromatic images with numbers</div>
  <div><button class="button" @click="handleSubmit">Submit</button></div>
</template>

<style scoped>
.grid-container {
  border: #3e8ed0;
  border-style: solid;
  border-width: 2px;
  border-radius: 10px;
  background-color: white;

  display: flex;
  flex-direction: column;
}

.row-container {
  display: flex;
}
</style>
