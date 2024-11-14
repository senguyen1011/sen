<script setup lang="ts">
  withDefaults(
    defineProps<{
      center?: boolean;
      size?: 1 | 2 | 3;
    }>(),
    {
      center: true
    }
  );
</script>

<template>
  <div
    class="container"
    :class="{
      'no-align': !center,
      'size-1': size === 1,
      'size-2': size === 2,
      'size-3': size === 3
    }"
  >
    <slot></slot>
  </div>
</template>

<style>
  :root {
    --size-1: 448px;
    --size-2: 688px;
    --size-3: 880px;
    --size-4: 1136px;
  }
  
  .container {
    width: 100%;
    margin: 0 auto;
  }

  .container.no-align {
    margin: 0;
  }

  @media (width <= 688px) {
    .container {
      max-width: var(--size-1);
    }
  }

  @media (width <= 880px) {
    .container {
      max-width: var(--size-2);

      &.size-1 {
        max-width: var(--size-1);
      }
    }
  }

  @media (width <= 1136px) {
    .container {
      max-width: var(--size-3);

      &.size-1 {
        max-width: var(--size-1);
      }
      &.size-2 {
        max-width: var(--size-2);
      }
    }
  }

  @media (width > 1136px) {
    .container {
      max-width: var(--size-4);

      &.size-1 {
        max-width: var(--size-1);
      }
      &.size-2 {
        max-width: var(--size-2);
      }
      &.size-3 {
        max-width: var(--size-3);
      }
    }
  }
</style>
