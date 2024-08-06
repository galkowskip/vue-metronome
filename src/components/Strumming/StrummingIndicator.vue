<template>
  <div class="strumming-indicator" :class="{
    'strumming-indicator--active': props.isActive,
    'strumming-indicator--up': props.isUp,
    'strumming-indicator--down': !props.isUp,
    'strumming-indicator--disabled': props.disabled,
  }">
    <div>{{ !props.disabled ? props.beatKey % 1 === 0.5 ? '+' : props.beatKey : '' }}</div>

    <div class="strumming-indicator__arrow"></div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  isActive: boolean;
  isUp: boolean;
  disabled?: boolean;
  beatKey: number;
}>();
</script>

<style scoped lang="scss">
.strumming-indicator {
  display: grid;
  grid-template-columns: 32px;
  grid-template-rows: 32px 32px;
  gap: 4px;
  font-size: 0.8rem;

  &__arrow {
    width: 16px;
    height: 8px;
    background-color: #f0f0f0;
    border: 1px solid #f00;
    transition: background-color 0.1s;
  }

  &--active:not(.strumming-indicator--disabled) {
    .strumming-indicator {
      &__arrow {
        background-color: #f00;
      }
    }
  }

  &--down {
    .strumming-indicator {
      &__arrow {
        transform: rotate(-45deg);
      }
    }
  }

  &--up {
    .strumming-indicator {
      &__arrow {
        transform: rotate(45deg);
      }
    }
  }

  &--disabled {
    .strumming-indicator {
      &__arrow {
        background-color: #f0f0f0;
      }
    }
  }
}
</style>