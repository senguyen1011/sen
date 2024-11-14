<script setup lang="ts">
  import Container from '@/components/Container.vue';
  import ScrollText from '@/components/animation/ScrollText.vue';
  import BlurIn from '@/components/animation/BlurIn.vue';
  import ArrowDown from '@/components/icons/ArrowDown.vue';
  // defineProps<{
  //   msg: string
  // }>()
</script>

<template>
  <section id="landing">
    <Container id="landing-hero">
      <hgroup>
        <span class="landing-display">
          <BlurIn :duration="800">
            <ScrollText
              id="first-name"
              value="Sean"
              :duration="800"
            />
          </BlurIn>
          <BlurIn
            :duration="800"
            :delay="150"
          >
            <ScrollText
              id="last-name"
              value="Nguyen"
              :duration="800"
              :delay="150"
            />
          </BlurIn>
          <BlurIn
            :duration="600"
            :delay="150"
          >
            <span class="landing-subtitle">
              <h6 id="year">2025</h6>
              <h6 id="subtitle">Portfolio Site</h6>
            </span>
          </BlurIn>
        </span>
      </hgroup>
    </Container>
    <Container id="landing-footer">
      <div class="lead">
        <ArrowDown />
        <span>
          <p>You can scroll</p>
          <p>if you want to</p>
        </span>
      </div>
      <a href="#">Resume</a>
      <span class="end">
        <p>Quality Engineer &</p>
        <p>Front End Developer</p>
      </span>
    </Container>
    <div id="background"></div>
  </section>
</template>

<style scoped>
  #landing {
    height: 100vh;
    display: flex;
    flex-direction: column;
    text-transform: uppercase;

    #background {
      position: absolute;
      height: 100%;
      width: 100%;
      background: 
        radial-gradient(at 100% 75%, #524202 0px, transparent 50%),
        radial-gradient(at 10% 25%, #362b00 0px, transparent 50%) var(--background-2);

      background-size: 200% 200%;
      animation: gradient-ambient 30s linear infinite;
      z-index: -2;
    }

    #landing-hero {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;

      hgroup {
        width: 100%;
        height: 3em;
        min-height: calc(3em + --nav-height);
        padding-top: var(--nav-height);
        font-size: 10rem;
      }

      .landing-display {
        position: relative;
        width: 100%;
        color: var(--text-1);
        white-space: nowrap;

        h6 {
          margin: 0;
        }

        #first-name,
        #last-name {
          font-weight: 700;
        }

        #first-name {
          position: absolute;
          top: 0;
          left: 0;
          font-size: inherit;
        }

        #last-name {
          position: absolute;
          top: 0.775em;
          left: 2.05625em;
          font-size: inherit;
        }

        .landing-subtitle {
          position: absolute;
          top: 1.415em;
          left: 0.03125em;
          color: var(--accent-text-2);

          h6 {
            font-size: var(--font-size-4);
          }
        }
      }
    }

    #landing-footer {
      height: var(--nav-height);
      display: flex;
      justify-content: space-between;
      align-items: center;

      color: var(--text-2);

      p {
        margin: 0;
      }

      .lead {
        display: inline-flex;
        gap: var(--space-2);
        text-align: left;

        svg {
          width: 2rem;
          height: 2rem;

          animation: blink 1s linear alternate infinite;

        }
      }
      .end {
        text-align: right;
      }
    }
  }

  @keyframes gradient-ambient {
    0% {
      background-position: 50% 50%;
    }
    33% {
      background-position: 0% 100%;
    }
    66% {
      background-position: 100% 0%;
    }
    100% {
      background-position: 50% 50%;
    }
  }

  @keyframes blink {
    0% {
      opacity: 0
    }
    100% {
      opacity: 1
    }
  }
</style>
