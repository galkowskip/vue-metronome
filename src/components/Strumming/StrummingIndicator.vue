<template>
    <div class="strumming-indicator"
        :class="{
            'strumming-indicator--active': props.isActive,
            'strumming-indicator--up': props.isUp,
            'strumming-indicator--down': !props.isUp,
            'strumming-indicator--disabled': props.disabled
        }"
    >
    </div>
</template>

<script setup lang="ts">
const props = defineProps<{
    isActive: boolean;
    isUp: boolean;
    disabled?: boolean;
}>()
</script>

<style scoped lang="scss">
.strumming-indicator {
    width: 16px;
    height: 8px;
    background-color: #f0f0f0;
    border: 1px solid #f00;
    transition: background-color 0.1s;


    &--active {
        background-color: #f00;
    }
    &--up {
        transform: rotate(-45deg);
    }
    &--down {
        transform: rotate(45deg);
    }
    &--disabled {
        background-color: #f0f0f0;
    }
}
</style>