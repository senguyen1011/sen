<script setup lang="ts">
  import NavBar from '@/components/NavBar.vue';
  import Landing from '@/pages/Landing.vue';
</script>

<template>
  <div class="bg-line" />
  <NavBar
    :paths="[
      { name: 'about', path: '#about' },
      { name: 'work', path: '#work' },
      { name: 'misc', path: '#misc' },
      { name: 'contact', path: '#contact' }
    ]"
  />
  <Landing />

</template>

<style>
  #root {
    position: relative;
  }
  .bg-line {
    position: absolute;
    top: 0;
    left: 1rem;
    height: 100%;
    width: 1px;
    background-color: var(--border-1);
    z-index: -1;
  }

  @media (width <= 688px) {
    .bg-line {
      left: calc((100% - var(--size-1) )/ 2 + 1rem);
    }
  }

  @media (width <= 880px) {
    .bg-line {
      left: calc((100% - var(--size-2) )/ 2 + 1rem);
    }
  }

  @media (width <= 1136px) {
    .bg-line {
      left: calc((100% - var(--size-3) )/ 2 + 1rem);
    }
  }

  @media (width > 1136px) {
    .bg-line {
      left: calc((100% - var(--size-4) )/ 2 + 1rem);
    }
  }
</style>
