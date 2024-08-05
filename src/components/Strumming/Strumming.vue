<template>
    <div class="strumming-container">
        {{ currentBeat }}
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    currentBeat: number;
}>()



</script>