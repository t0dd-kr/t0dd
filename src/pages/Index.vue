<script setup lang="ts">
  import RainbowText from '@/components/RainbowText.vue'
  import { ref } from 'vue'
  let splineLoaded = ref(false)

  let interval = setInterval(() => {
    if(window.hasOwnProperty('isSplineAppLoaded')) {
      splineLoaded.value = true
      clearInterval(interval);
    }
  }, 500)
</script>

<template>
  <main>
    <section>
      <div class="flex">
        <figure class="container-canvas">
          <img src="@/assets/t_3d.png" alt="t0dd">
          <canvas id="canvas3d"></canvas>
        </figure>
        <article id="about">
          <h1>
            <RainbowText letters="Hello,"/>
            <br>
            <RainbowText letters="I'm t0dd."/>
          </h1>
          <div class="introduce">
            <RainbowText letters="I'm Web Developer who loves Javascript ecosystem."/>
          </div>
          <div class="container-icons">
            <a href="https://github.com/t0dd-kr" target="__blank" name="github">
              <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M29.3609 35C12.8491 32.5 14.1192 21.25 19.1997 17.5C18.197 15.9789 16.6594 10 17.9295 7.50003C20.4698 8.75 23.8793 10.5986 25.5504 12.5C30.631 10 38.2518 10 42.0623 12.5C43.0649 10.4718 46.7419 8.55634 48.413 7.5C49.917 9.02113 48.8308 14.9648 48.413 17.5C50.9196 22.993 52.2235 31.25 38.2518 35C40.9475 37.1811 45.7836 43.3079 47.7205 49.4971C48.1534 50.8804 46.8374 52.0671 45.4267 51.7341C42.3129 50.9991 37.3176 50 33.1714 50C28.724 50 22.1317 51.1495 18.3483 51.8896C16.9413 52.1649 15.7393 50.9447 16.256 49.6073C17.5807 46.1788 20.1145 41.8998 23.0102 40C22.3836 39.1549 19.9012 36.7218 15.3893 38.75C9.74948 41.2852 6.51518 35.669 7.76848 32.5" stroke="black" stroke-width="5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <label for="github"></label>
            </a>

            <a href="mailto:t0dd@t0dd.kr" name="mail">
              <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M7.5 32.5L7.5 15.2062C7.5 12.9584 9.8927 11.694 11.5348 13.074L23.8606 23.4322C27.4717 26.4669 32.5283 26.4669 36.1394 23.4322L48.4652 13.074C50.1073 11.694 52.5 12.9584 52.5 15.2062V44.7988C52.5 46.2906 51.3807 47.5 50 47.5L10 47.5C8.61929 47.5 7.5 46.2906 7.5 44.7988L7.5 40" stroke="black" stroke-width="5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <label for="mail"></label>
            </a>

            <a href="https://about.t0dd.kr" target="__blank" name="notion">
              <svg width="60" height="60" viewBox="0 0 60 60" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M40.3 24.2257V44.2367L37.95 44.4856L26.6 24.823L24.5 25.0221V52.5L50 50.708V15.1641L38.35 7.5L7.5 10.2422V42.8429L15.8 52.5V17.7656L40.3 15.7958" stroke="black" stroke-width="5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              <label for="notion"></label>
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
    justify-content: center;
    align-items: center;
    @media (max-width: 1100px) {
      align-items: flex-start;
      @media (max-width: 600px) {
        padding-top: 30px;
        box-sizing: border-box;
      }
    }
  }

  figure {
    margin: 0;
  }

  article#about {
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

    h1 { 
      font-size: 1.5em;
      margin: 2vh 0;
      @media (max-width: 1100px) {
        font-size: 8vw;
        & br {
          display: none;
        }
        margin-top: 0;
      }
    }
    .introduce { 
      margin-bottom: 1.33em;
      @media (max-width: 1100px) {
        margin-bottom: 1em;
        font-size: 6vw;
      }
    }
  }

  .flex {
    display: flex;
  }

  .container-canvas {
    position: relative;
    width: 500px;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: center;
    
    @media (max-width: 1100px) {
      max-width: 450px;
      max-height: 450px;
      padding: 0 75px;
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
        max-width: 450px;
        max-height: 450px;
        width: 100vw;
        height: 100vw;
        box-sizing: border-box;
      }
    }

    & #canvas3d { 
      position: absolute;
      top: 0;
      left: 0;
      width: 100% !important;
      height: 100% !important;
    }
  }

  .container-icons {
    & svg {
      @media (max-width: 600px) {
        width: 40px;
        height: 40px;
      }
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