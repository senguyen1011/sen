<script setup lang="ts">
  import Container from './Container.vue';
  interface path {
    name: string;
    path: string;
  }

  defineProps<{
    paths: path[];
  }>();
</script>

<template>
  <nav id="top-nav">
    <Container>
      <h1 id="brand">Sen</h1>
      <ul
        v-motion 
        :initial="{ opacity: 0, y: -50 }"
        :enter="{ opacity: 1, y: 0, transition: {
          duration: 200,
          ease: 'easeInOut'
        }}"
      >
        <li v-for="path in paths">
          <a :href="path.path">
            {{ path.name }}
          </a>
        </li>
      </ul>
    </Container>
  </nav>
</template>

<style>
  :root {
    --nav-height: 6rem;
  }

  #top-nav {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: var(--nav-height);

    text-transform: uppercase;
    z-index: 100;

    .container {
      height: 100%;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    #brand {
      margin: 0;
      font-size: var(--font-size-8);
      letter-spacing: var(--letter-space-8);
      color: var(--accent-text-2);
    }

    ul {
      padding: var(--space-5);
      display: flex;
      justify-content: center;
      align-items: center;
      gap: var(--space-4);
      background-color: var(--background-glass);
      border-radius: 9999px;

      list-style-type: none;
      margin-block-start: 0;
      margin-block-end: 0;

      li {
        height: 100;
        display: inline-flex;
        justify-content: center;
        align-items: center;
        text-align: center;
      }

      a {
        transition: color 150ms ease-in-out;
      }
    }
  }
</style>
