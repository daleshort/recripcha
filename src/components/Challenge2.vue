<script setup>
import { ref } from "vue";
import PhotoSquare from "./PhotoSquare.vue";

const emit = defineEmits(["submit"]);
const selectStatus = ref(Array(10).fill(false));
var arr = [];

const answerKey = [
  false,
  false,
  false,
  false,
  false,
  false,
  false,
  false,
  true,
  true,
];
while (arr.length < 9) {
  var r = Math.floor(Math.random() * 9) + 1;
  if (arr.indexOf(String(r)) === -1) {
    arr.push(String(r));
  }
}

const handleSquareClick = ({ value }, dotNumber) => {
  console.log("dot number", dotNumber);

  selectStatus.value[parseInt(dotNumber)] = value;
  console.log("select status", selectStatus.value);
};
const handleSubmit = () => {
  const isCorrect =
    selectStatus.value.length === answerKey.length &&
    selectStatus.value.every((value, index) => value === answerKey[index]);

  emit("submit", isCorrect);
};

console.log(arr);
</script>

<template>
  <div class="grid-container">
    <div class="row-container">
      <PhotoSquare
        :dotNumber="arr[0]"
        @squareClick="handleSquareClick"
      /><PhotoSquare
        :dotNumber="arr[1]"
        @squareClick="handleSquareClick"
      /><PhotoSquare :dotNumber="arr[2]" @squareClick="handleSquareClick" />
    </div>
    <div class="row-container">
      <PhotoSquare
        :dotNumber="arr[3]"
        @squareClick="handleSquareClick"
      /><PhotoSquare
        :dotNumber="arr[4]"
        @squareClick="handleSquareClick"
      /><PhotoSquare :dotNumber="arr[5]" @squareClick="handleSquareClick" />
    </div>
    <div class="row-container">
      <PhotoSquare
        :dotNumber="arr[6]"
        @squareClick="handleSquareClick"
      /><PhotoSquare
        :dotNumber="arr[7]"
        @squareClick="handleSquareClick"
      /><PhotoSquare :dotNumber="arr[8]" @squareClick="handleSquareClick" />
    </div>
  </div>
  <div class="mt-2 mb-2">Select all accessible entrances</div>
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
