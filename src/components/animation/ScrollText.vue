<!-- 
* Inspired by Hyper Text component from Inspira UI
* https://inspira-ui.com/components/hyper-text
-->

<script setup lang="ts">
  import { ref, computed, watch } from 'vue';
  import { useIntervalFn } from '@vueuse/core';

  const props = defineProps({
    value: {
      type: String,
      required: true
    },
    duration: {
      type: Number,
      default: 100
    },
    delay: {
      type: Number,
      default: 0
    },
    triggerOnHover: {
      type: Boolean,
      default: true
    }
  });

  const randomChars = 'abcdefghijklmnopqrstuvwxyz1234567890';
  const displayChars = ref(props.value.split(''));
  const charInd = ref(0);

  function triggerAnimation() {
    charInd.value = 0;
    startAnimation();
  }

  const { pause, resume } = useIntervalFn(
    () => {
      if (charInd.value < props.value.length) {
        displayChars.value = displayChars.value.map((char, ind) =>
          char === ' '
            ? char
            : ind <= charInd.value
            ? props.value[ind]
            : randomChars[Math.floor(Math.random() * randomChars.length)]
        );
        charInd.value += 0.1;
      } else {
        pause();
      }
    },
    computed(() => props.duration / (props.value.length * 10))
  );

  function startAnimation() {
    pause();
    resume();
  }

  function hoverAnimation() {
    if (props.triggerOnHover) {
      triggerAnimation()
    }
  }

  watch(
    () => props.value,
    res => {
      displayChars.value = res.split('');
      triggerAnimation();
    }
  );

  setTimeout(() => triggerAnimation(), props.delay);
</script>

<template>
  <div
    class="scroll-text-wrapper"
    @mouseenter="hoverAnimation"
  >
    <span
      v-for="(char, ind) in displayChars"
      :key="`${value}-${ind}`"
      v-motion
      :initial="{ opacity: 0, y: 100 }"
      :enter="{
        opacity: 1,
        y: 0,
        transition: {
          type: 'keyframes',
          ease: 'easeInOut'
        }
      }"
      :delay="delay + ind * (duration / (value.length * 10))"
    >
      {{ char }}
    </span>
  </div>
</template>

<style>
  .scroll-text-wrapper {
    display: inline-flex;
  }
</style>
