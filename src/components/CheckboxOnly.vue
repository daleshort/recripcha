<script setup>
import { ref } from "vue";
const emit = defineEmits(["changeCheckStatus"]);
const isChecked = ref(false);

const handleClick = (event) => {
  isChecked.value = !isChecked.value;
  emit("changeCheckStatus", isChecked.value);
};
</script>

<template>
  <div>
    <label for="status_checkbox" class="checkbox ">
      <input
        type="checkbox"
        class="checkbox"
        id="status_checkbox"
        :checked="isChecked"
        @change="handleClick"
      />
      I'm Disabled</label
    >
  </div>
</template>

<style scoped></style>
