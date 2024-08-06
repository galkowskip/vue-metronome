<template>
  <div class="strumming-indicator" :class="{
    'strumming-indicator--active': props.isActive,
    'strumming-indicator--up': props.isUp,
    'strumming-indicator--down': !props.isUp,
    'strumming-indicator--disabled': props.disabled,
  }">
    <div>{{ props.beatKey % 1 === 0.5 ? '+' : props.beatKey }}</div>

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
    position: relative;

    &::after {
      content: "";
      position: absolute;
      width: 0;
      height: 0;
      border-left: 8px solid transparent;
      border-right: 8px solid transparent;
      border-bottom: 8px solid #f0f0f0;
      top: 0;
      left: 0;
    }

    &::before {
      content: "";
      position: absolute;
      width: 0;
      height: 0;
      border-left: 8px solid transparent;
      border-right: 8px solid transparent;
      border-bottom: 8px solid #f0f0f0;
      top: 0;
      left: 0;
    }
  }

  &--active:not(.strumming-indicator--disabled) {
    .strumming-indicator {
      &__arrow {
        &::after {
          border-bottom-color: #f00;
        }
      }
    }
  }

  &--down {
    .strumming-indicator {
      &__arrow {
        transform: rotate(180deg);
      }
    }
  }

  &--up {
    .strumming-indicator {
      &__arrow {
        transform: rotate(0deg);
      }
    }
  }

  &--disabled {
    .strumming-indicator {
      &__arrow {
        display: none;
      }
    }
  }
}
</style>