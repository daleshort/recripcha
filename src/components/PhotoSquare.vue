<script setup>
import { ref } from "vue";

const props = defineProps({
  dotNumber: String,
});
const emit = defineEmits(["squareClick"]);

const isSelected = ref(false);
const handleClick = () => {
  isSelected.value = !isSelected.value;
  emit("squareClick", isSelected, props.dotNumber);
};
</script>

<template>
  <div :class="{ 'is-selected': isSelected }">
    <img
      :src="`./assets/access${dotNumber}.jpeg`"
      @pointerdown="handleClick"
      draggable="false"
      :class="{ opacity: isSelected }"
    />
  </div>
</template>

<style scoped>
div {
  border: rgba(30, 188, 19, 0);
  border-width: 3px;
  border-style: solid;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  box-sizing: border-box;
  margin: 3px;

  max-width: 150px;
  max-height: 150px;
}

.is-selected {
  border: #3e8ed0;
  border-width: 2px;
  border-style: solid;
}

img {
  min-width: 100%;
  min-height: 100%;
}

.opacity {
  filter: opacity(0.7);
}
</style>
