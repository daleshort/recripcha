<script setup>
import Checkbox from "./components/Checkbox.vue";
import Challenge from "./components/Challenge.vue";
import Challenge2 from "./components/Challenge2.vue";
import Challenge3 from "./components/Challenge3.vue";
import CripSpinner from "./components/CripSpinner.vue";
import CheckboxOnly from "./components/CheckboxOnly.vue";
import AbleistScum from "./components/AbleistScum.vue";
import Welcome from "./components/Welcome.vue";

import ChallengeStatus from "./components/ChallengeStatus.vue";
import "bulma/css/bulma.css";

import { ref } from "vue";

const status = ref("Waiting for Input");
const spinnerStatus = ref(0);

const maxChallengeId = 2;

const getRandomStart = () => {
  return Math.floor(Math.random() * maxChallengeId);
};
const challengeId = ref(getRandomStart());

const handleChallengeSubmit = (isCorrect) => {
  if (isCorrect) {
    status.value = "Welcome";
    spinnerStatus.value = 0;
  } else {
    status.value = "Ableist Scum Detected";
  }
  challengeId.value += 1;
  if (challengeId.value > maxChallengeId) {
    challengeId.value = 0;
  }
};

function delay(duration) {
  return new Promise((resolve) => {
    setTimeout(resolve, duration);
  });
}

const handleCheckbox = (isChecked) => {
  if (isChecked) {
    spinnerStatus.value = 1;
    Promise.resolve()
      .then(() => delay(1000))
      .then(() => {
        spinnerStatus.value = 2;
      })
      .then(() => delay(200))
      .then(() => {
        spinnerStatus.value = 3;
      })
      .then(() => delay(200))
      .then(() => {
        status.value = "Please Verify Your Disability Status";
      });
  } else {
    status.value = "Waiting for Input";
    spinnerStatus.value = 0;
  }
};
</script>

<template>
  <header></header>

  <div
    class="box container main-container is-max-desktop is-flex is-align-items-center is-flex-direction-column has-background-info-light mt-5"
  >
    <div class="checkbox-container mb-4">
      <h1 class="title mb-0">re<span class="title-highlight">Crip</span>cha</h1>
      <CripSpinner :loadState="spinnerStatus"></CripSpinner>
    </div>

    <CheckboxOnly @changeCheckStatus="handleCheckbox" />

    <ChallengeStatus
      v-if="status != 'Waiting for Input'"
      :statusText="status"
    />
    <Challenge
      v-if="
        status == 'Please Verify Your Disability Status' && challengeId == 0
      "
      @submit="handleChallengeSubmit"
    />
    <Challenge2
      v-if="
        status == 'Please Verify Your Disability Status' && challengeId == 1
      "
      @submit="handleChallengeSubmit"
    />
    <Challenge3
      v-if="
        status == 'Please Verify Your Disability Status' && challengeId == 2
      "
      @submit="handleChallengeSubmit"
    />
    <Welcome v-if="status == 'Welcome'" />
    <AbleistScum v-if="status == 'Ableist Scum Detected'" />
  </div>
</template>

<style scoped>
.main-container {
  max-width: 600px;
  min-height: 600px;
}
.checkbox-container {
  display: flex;
  align-items: center;
  justify-items: center;
  flex-direction: row;
}
</style>
