<template>
  <main>
    <div class="main-container">
      <BeatController />
    </div>
  </main>
</template>

<script setup lang="ts">
import Metronome from "@/components/Metronome/Metronome.vue";
import BeatController from "./components/BeatController.vue";
</script>

<style scoped>
.main-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
}
</style>
