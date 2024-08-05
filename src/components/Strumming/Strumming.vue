<template>
  <div class="strumming-container">
    <StrummingIndicator
      v-for="i in 8"
      :key="i"
      :isUp="i % 2 === 0"
      :isActive="currentBeat - 1 === i"
    />
  </div>
</template>

<script setup lang="ts">
import StrummingIndicator from "./StrummingIndicator.vue";

const props = defineProps<{
  currentBeat: number;
}>();
</script>

<style scoped lang="scss">
.strumming-container {
  display: flex;
  gap: 8px;
}
</style>