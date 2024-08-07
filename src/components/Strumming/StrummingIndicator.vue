<template>
  <div class="strumming-indicator" :class="{
    'strumming-indicator--active': props.isActive,
    'strumming-indicator--up': props.isUp,
    'strumming-indicator--down': !props.isUp,
    'strumming-indicator--disabled': props.disabled,
  }" @click="toggleStrum">
    <div class="strumming-indicator__number">{{ props.beatKey % 1 === 0.5 ? '+' : props.beatKey }}</div>

    <div class="strumming-indicator__arrow">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 32 32">
        <path d="m26.71 10.29-10-10a1 1 0 0 0-1.41 0l-10 10 1.41 1.41L15 3.41V32h2V3.41l8.29 8.29z" />
      </svg>


    </div>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  isActive: boolean;
  isUp: boolean;
  disabled?: boolean;
  beatKey: number;
}>();

const emit = defineEmits();

const toggleStrum = () => {
  emit('toggleStrum', props.beatKey);
};
</script>

<style scoped lang="scss">
.strumming-indicator {
  display: grid;
  grid-template-columns: 32px;
  grid-template-rows: 32px 32px;
  gap: 4px;
  font-size: 0.8rem;
  padding: 4px;
  border: 1px solid transparent;
  border-radius: 4px;
  transition: border 0.1s;

  &:hover {
    cursor: pointer;

    border: 1px solid #fff;
  }

  &__number {
    display: flex;
    justify-content: center;
    align-items: center;
  }

  &__arrow {
    position: relative;
    color: #fff;

    svg {
      stroke: #fff;
      fill: #fff;
    }
  }

  &--active {
    &:not(.strumming-indicator--disabled) {
      .strumming-indicator__arrow {
        svg {
          stroke: #f00;
          fill: #f00;
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
        svg {
          stroke: transparent;
          fill: transparent;
        }
      }


    }
  }
}
</style>