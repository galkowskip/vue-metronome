<template>
  <div class="slider-container">
    <input
      type="range"
      :min="min"
      :max="max"
      :value="value"
      @input="$emit('update:modelValue', $event.target.value)"
    />
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  min: number;
  max: number;
}>();

const value = defineModel({});
</script>
