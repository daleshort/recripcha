<script setup>
import { ref } from "vue";
defineProps({});
const emit = defineEmits(["changeCheckStatus"]);
const loadState = ref(0);
const isChecked = ref(false);

function delay(duration) {
  return new Promise((resolve) => {
    setTimeout(resolve, duration);
  });
}

const handleClick = (event) => {
  isChecked.value = !isChecked.value;
  if (isChecked.value == true) {
    loadState.value = 1;
    console.log(isChecked.value);

    Promise.resolve()
      .then(() => delay(1000))
      .then(() => {
        loadState.value = 2;
      })
      .then(() => delay(200))
      .then(() => {
        loadState.value = 3;
      })
      .then(() => delay(200))
      .then(() => {
        emit("changeCheckStatus", isChecked.value);
      });
  } else {
    loadState.value = 0;
    emit("changeCheckStatus", isChecked.value);
  }
};

const getClassForLoadState = () => {
  if (loadState.value == 0) {
    return "";
  } else if (loadState.value == 1) {
    return "spinner-active";
  } else if (loadState.value == 2) {
    return "spinner-shrink";
  } else if (loadState.value == 3) {
    return "spinner-expand";
  }
};
const getIconForLoadState = () => {
  if (loadState.value == 0) {
    return "icon";
  } else if (loadState.value == 1) {
    return "icon";
  } else if (loadState.value == 2) {
    return "icon";
  } else if (loadState.value == 3) {
    return "x";
  }
};
</script>

<template>
  <div class="checkbox-container">
    <div>
      <label for="status_checkbox" class="checkbox">
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
  </div>
</template>

<style scoped>
.icon-loading {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 4px;
  margin-right: 4px;
  min-width: 60px;
  min-height: 60px;
}

.checkbox-container {
  display: flex;
  align-items: center;

  flex-direction: row;
}
</style>
