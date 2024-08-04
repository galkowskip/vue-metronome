<template>
  <main>
    <div class="main-container">
      <Metronome />
    </div>
  </main>
</template>

<script setup lang="ts">
import Metronome from "./components/Metronome.vue";
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
