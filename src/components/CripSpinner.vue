<script setup>
import { ref } from "vue";
const props = defineProps({ loadState: { type: Number, required: true } });


const getClassForLoadState = () => {
  if (props.loadState == 0) {
    return "";
  } else if (props.loadState == 1) {
    return "spinner-active";
  } else if (props.loadState == 2) {
    return "spinner-shrink";
  } else if (props.loadState == 3) {
    return "spinner-expand";
  }
};
const getIconForLoadState = () => {
  if (props.loadState == 0) {
    return "icon";
  } else if (props.loadState == 1) {
    return "icon";
  } else if (props.loadState == 2) {
    return "icon";
  } else if (props.loadState == 3) {
    return "x";
  }
};
</script>

<template>
  <div class="icon-loading">
    <font-awesome-icon
      class="spinner"
      :class="getClassForLoadState()"
      icon="fa-brands fa-accessible-icon"
      v-if="getIconForLoadState() == 'icon'"
      draggable="false"
      color="blue"
    />
    <font-awesome-icon
      class="spinner"
      :class="getClassForLoadState()"
      icon="fa-solid fa-circle-xmark"
      v-if="getIconForLoadState() == 'x'"
      draggable="false"
      color="blue"
    />
  </div>
</template>

<style scoped>
.icon-loading {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 4px;
  margin-right: 4px;
  min-width: 40px;
  min-height: 40px;
}

.checkbox-container {
  display: flex;
  align-items: center;

  flex-direction: row;
}
</style>
