<template>
  <div class="strumming-container">
    <StrummingDouble v-for="i in beatsInBar" :key="i" :currentBeat="currentBeat" :beatKey="i" />
  </div>
</template>

<script setup lang="ts">
import StrummingDouble from "./StrummingDouble.vue";

const props = defineProps<{
  currentBeat: number;
  beatsInBar: number
}>();
</script>

<style scoped lang="scss">
.strumming-container {
  display: flex;
  gap: 8px;
}
</style>