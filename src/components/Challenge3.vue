<script setup>
import { ref } from "vue";
import PhotoSquare from "./PhotoSquare.vue";

const emit = defineEmits(["submit"]);
const formText = ref("");

const answerKey = ref("I am not ableist scum");

const handleSubmit = () => {
  const isCorrect = formText.value == answerKey.value;
  emit("submit", isCorrect);
};
</script>

<template>
  <div>
    <img
      :src="`./assets/black.jpeg`"
      :alt="'An image displaying text: ' + answerKey"
    />
  </div>
  <div class="form-container">
    <div class="mt-2 mb-2">Enter the text in the image above</div>
    <div>
      <input
        class="input"
        type="text"
        v-model="formText"
        placeholder="Enter Image Text"
      />
    </div>
    <div class="mt-2">
      <button class="button" @click="handleSubmit">Submit</button>
    </div>
  </div>
</template>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.row-container {
  display: flex;
}
</style>
