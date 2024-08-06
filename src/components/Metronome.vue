<template>
  <div class="metronome">
    <MetronomeIndicator :isBeat="isBeat" />
    <MetronomeControls v-model:isPlaying="isPlaying" v-model:bpm="bpm" />
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";

import MetronomeControls from "@/components/Metronome/MetronomeControls.vue";
import MetronomeIndicator from "@/components/Metronome/MetronomeIndicator.vue";

const emit = defineEmits(["beat"]);

const bpm = ref(120);
const isPlaying = ref(false);

const isBeat = ref(false);
const timer = ref<number | undefined>(undefined);

const play = () => {
  const interval = (60 / bpm.value) * 1000;
  timer.value = setInterval(() => {
    isBeat.value = true;
    setTimeout(() => {
      isBeat.value = false;
    }, 100);
  }, interval);
};

watch(isPlaying, (newIsPlaying) => {
  if (newIsPlaying) {
    play();
  } else {
    clearInterval(timer.value);
  }
});

watch(bpm, (newBpm) => {
  if (isPlaying.value) {
    clearInterval(timer.value);
    play();
  }
});

watch(isBeat, (value) => {
  emit("beat", value);
});
</script>

<style scoped lang="scss">
.metronome {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}
</style>
