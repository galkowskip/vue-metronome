<template>
  <div class="metronome-controls">
    <Slider v-model="bpm" :min="60" :max="240" />
    <div class="metronome-controls__actions">
      <button @click="resetBpm">Reset</button>
      <h2>{{ bpm }}</h2>
      <button @click="togglePlay">{{ isPlaying ? "Stop" : "Play" }}</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import Slider from "./Slider.vue";

const bpm = defineModel("bpm", {
  default: 120,
  emits: ["update:bpm"],
});
const isPlaying = defineModel("isPlaying", {
  default: false,
  emits: ["update:isPlaying"],
});

const resetBpm = () => {
  bpm.value = 120;
};

const togglePlay = () => {
  isPlaying.value = !isPlaying.value;
};
</script>

<style scoped lang="scss">
.metronome-controls {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  &__actions {
    display: flex;
    gap: 1rem;
  }
}
</style>
