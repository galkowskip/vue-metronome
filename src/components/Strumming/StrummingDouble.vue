<template>
    <div class="strumming-double">
        <StrummingIndicator :isActive="currentBeat === beatKey" :isUp="false" :beatKey="beatKey" />
        <StrummingIndicator :isActive="currentBeat - 0.5 === beatKey" :isUp="true" :beatKey="beatKey - 0.5" />
    </div>
</template>

<script setup lang="ts">
import StrummingIndicator from './StrummingIndicator.vue';

const props = defineProps<{
    currentBeat: number;
    beatKey: number;
}>();

</script>

<style scoped lang="scss">

.strumming-double {
    display: flex;
    gap: 8px;
}

</style>