<template>
  <div
    class="metronome-indicator"
    :class="{ 'metronome-indicator--beat': props.isBeat }"
  ></div>
</template>

<script setup lang="ts">
const props = defineProps<{
  isBeat: boolean;
}>();
</script>

<style scoped lang="scss">
.metronome-indicator {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background-color: #f0f0f0;
  border: 1px solid #f00;
  transition: background-color 0.1s;
  &--beat {
    background-color: #f00;
  }
}
</style>
