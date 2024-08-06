<template>
    <div class="strumming-double">
        <StrummingIndicator :isActive="currentBeat === beatKey" :isUp="false" :beatKey="beatKey" :disabled="!strumPattern.down"/>
        <StrummingIndicator :isActive="currentBeat - 0.5 === beatKey" :isUp="true" :beatKey="beatKey - 0.5" :disbled="!strumPattern.up" />
    </div>
</template>

<script setup lang="ts">
import type { StrummingPattern } from '@/types/strumming.dto';
import StrummingIndicator from './StrummingIndicator.vue';

const props = defineProps<{
    currentBeat: number;
    beatKey: number;
    strumPattern: StrummingPattern;
}>();

</script>

<style scoped lang="scss">
.strumming-double {
    display: flex;
    gap: 8px;
}
</style>