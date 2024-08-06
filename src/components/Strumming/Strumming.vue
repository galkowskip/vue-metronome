<template>
  <div class="strumming-container">
    <StrummingDouble v-for="i in beatsInBar" :key="i" :currentBeat="currentBeat" :beatKey="i" :strumPattern="currentStrummingPattern[i - 1]" />
  </div>
</template>

<script setup lang="ts">
import type { StrummingPattern } from "@/types/strumming.dto";

import StrummingDouble from "./StrummingDouble.vue";


const props = defineProps<{
  currentBeat: number;
  beatsInBar: number
}>();

const currentStrummingPattern: StrummingPattern[] = [
  { up: false, down: true },
  { up: true, down: false },
  { up: false, down: true },
  { up: true, down: false },
];
</script>

<style scoped lang="scss">
.strumming-container {
  display: flex;
  gap: 8px;
}
</style>