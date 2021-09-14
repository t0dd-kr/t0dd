<script setup lang="ts">
  import { ref } from 'vue'
  let splineLoaded = ref(false)

  let interval = setInterval(() => {
    if(window.hasOwnProperty('isSplineAppLoaded')) {
      splineLoaded.value = true
      clearInterval(interval);
    }
  }, 500)

  function setup() {
    return { splineLoaded }
  }
</script>

<template>
  <main>
    <section>
      <div class="flex">
        <figure class="container-canvas">
          <img src="@/assets/t.svg" alt="t0dd" :class="[{ faded: splineLoaded }]">
          <canvas id="canvas3d" :class="[{ faded: !splineLoaded }]"></canvas>
        </figure>
        <article id="about">
          <h1>
            Hello, <br>
            I'm t0dd. <br>
          </h1>
          <h4>I'm Web Developer who loves Javascript ecosystem.</h4>
          <div class="container-icons">
            <a href="https://github.com/t0dd-kr" target="__blank">
              <svg id="github" width="40" height="42" viewBox="0 0 40 42" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M14.2857 32.381C7.14236 34.631 7.47569 27.7976 4.61903 27.0476M25.7142 39.0476V29.5476C25.7142 27.881 25.7602 26.706 24.7619 25.7143C29.4135 25.2143 33.3333 23.5567 33.3333 15.7667C33.3268 13.7602 32.5284 11.8375 31.1116 10.4167C31.4459 9.55586 31.6063 8.63731 31.5834 7.71415C31.5605 6.79099 31.3548 5.88152 30.9783 5.03833C30.9783 5.03833 29.2283 4.53833 25.185 7.15C21.7851 6.2638 18.2148 6.2638 14.815 7.15C10.77 4.53833 9.02162 5.03833 9.02162 5.03833C8.64506 5.88152 8.4394 6.79099 8.41651 7.71415C8.39363 8.63731 8.55398 9.55586 8.88829 10.4167C8.18148 11.1254 7.62143 11.9665 7.2402 12.892C6.85897 13.8175 6.66406 14.8091 6.66662 15.81C6.66662 23.5433 10.5864 25.1576 15.2381 25.7143C14.2531 26.696 14.1857 28.3526 14.2857 29.7143V39.0476" stroke="white" stroke-width="4" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </a>

            <a href="mailto:t0dd@t0dd.kr">
              <svg id="google" width="40" height="40" viewBox="0 0 40 40" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M31.5646 8.66902C28.626 5.6702 24.5303 3.80952 20 3.80952C11.0582 3.80952 3.80952 11.0582 3.80952 20C3.80952 28.9418 11.0582 36.1905 20 36.1905C28.9418 36.1905 36.1905 28.9418 36.1905 20H20.8095" stroke-width="4" stroke-linecap="round"/>
              </svg>
            </a>            
          </div>
        </article>
      </div>
    </section>
  </main>
</template>

<style lang="scss" scoped>
  main { 
    display: flex;
    flex-flow: column;
    width: 100%;
  }

  section {
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  #about {
    width: 500px;
    font-size: 32px;
    box-sizing: border-box;
    padding-left: 50px;

    @media (max-width: 1100px) {
      padding-left: 0px;
      
      @media (max-width: 600px) {
        width: 100%;
        max-width: 500px;
        padding: 0 20px;
        font-size: 24px;
      }
    }

    h1 { font-size: 1.5em }
  }

  .flex {
    display: flex;
  }

  figure {
    margin: 0;
  }

  .container-canvas {
    position: relative;
    width: 500px;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
    
    @media (max-width: 1100px) {
      max-width: 500px;
      max-height: 500px;
      padding: 0 50px;
      width: 100vw;
      height: 100vw;
      box-sizing: border-box;
    }

    & img {
      width: 500px;
      height: 500px;
      transition: opacity 1s;
      opacity: 1;
      @media (max-width: 1100px) {
        max-width: 500px;
        max-height: 500px;
        padding: 0 50px;
        width: 100vw;
        height: 100vw;
        box-sizing: border-box;
      }
      &.faded {
        opacity: 0;
      }
    }

    & #canvas3d { 
      position: absolute;
      top: 0;
      left: 0;
      width: 100% !important;
      height: 100% !important;

      transition: opacity 1s;
      opacity: 1;
      &.faded {
        opacity: 0;
      }
    }
  }
  .container-icons {
    & svg {
      margin-right: 20px;

      & path {
        stroke: #222;
        transition: stroke .15s;
      }

      &:hover path {
        stroke: #fff;
      }
    }
  }

  @media (max-width: 1100px) {
    section > .flex {
      flex-direction: column;
      align-items: center;
    }
  }
</style>