<template>
  <main>
    <div class="main-container">
      <BeatController />
    </div>
  </main>
</template>

<script setup lang="ts">
import BeatController from "./components/BeatController.vue";
</script>

<style scoped>
.main-container {
  display: flex;
  flex-direction: column;
  gap: 16px;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f0f0f0;
}
</style>
