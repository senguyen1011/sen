<!-- 
* Inspired by Blur Reveal component from Inspira UI
* https://inspira-ui.com/components/blur-reveal
-->

<script setup lang="ts">
  defineProps({
    duration: {
      type: Number,
      default: 500
    },
    delay: {
      type: Number,
      default: 0
    },
    blur: {
      type: Number,
      default: 24
    }
  });
</script>

<template>
  <div
    v-motion
    :initial="{ opacity: 0, filter: `blur(${blur}px)` }"
    :enter="{ opacity: 1, filter: 'blur(0px)' }"
    :duration="duration"
    :delay="delay"
  >
    <slot></slot>
  </div>
</template>
