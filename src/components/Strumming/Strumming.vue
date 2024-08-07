<template>
  <div class="strumming-container">
    <StrummingDouble @toggleStrum="toggleStrum" v-for="i in beatsInBar" :key="i" :currentBeat="currentBeat" :beatKey="i"
      :strumPattern="currentStrummingPattern[i - 1]" />
  </div>
</template>

<script setup lang="ts">
import type { StrummingPattern } from "@/types/strumming.dto";
import { ref } from "vue";

import StrummingDouble from "./StrummingDouble.vue";


const props = defineProps<{
  currentBeat: number;
  beatsInBar: number
}>();

const currentStrummingPattern = ref<StrummingPattern[]>([
  { down: true, up: false },
  { down: true, up: true },
  { down: true, up: false },
  { down: true, up: true },
]);

const toggleStrum = (value: number) => {
  const targetDouble = value % 1 === 0 ? value - 1 : value - 0.5
  const direction = value % 1 === 0 ? 'down' : 'up'

  console.log(targetDouble, direction)

  currentStrummingPattern.value[targetDouble][direction] = !currentStrummingPattern.value[targetDouble][direction]
};
</script>

<style scoped lang="scss">
.strumming-container {
  display: flex;
}
</style>