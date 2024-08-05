<template>
  <Metronome @beat="countBeat" @reset="resetBeat" />
  <Strumming :currentBeat="currentBeat" />
</template>

<script setup lang="ts">
import { ref } from "vue";

import Metronome from "@/components/Metronome/Metronome.vue";
import Strumming from "@/components/Strumming/Strumming.vue";

const currentBeat = ref(0);

const countBeat = (isMainBeat: boolean) => {
  if (isMainBeat) {
    if (currentBeat.value >= 4) {
      currentBeat.value = 1;
    } else {
      currentBeat.value += 0.5;
    }
  } else {
    currentBeat.value += 0.5;
  }
};

const resetBeat = () => {
  currentBeat.value = 0;
};
</script>