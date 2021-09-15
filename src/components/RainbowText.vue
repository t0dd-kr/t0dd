<script setup lang="ts">
  import anime from 'animejs';

  const props = defineProps({
    letters: null
  })

  function startAnimation(e :any) {
    let rainbowAnimation = anime({
      targets: [e.target],
      duration: 1000,
      loop: true,
      keyframes: [
        { color: 'rgb(255,0,0)' },
        { color: 'rgb(255,127,0)' }, 
        { color: 'rgb(255,127,0)' },
        { color: 'rgb(255,255,0)' },
        { color: 'rgb(127,255,0)' },
        { color: 'rgb(0,255,0)' },
        { color: 'rgb(0,255,127)' },
        { color: 'rgb(0,255,255)' },
        { color: 'rgb(0,127,255)' },
        { color: 'rgb(0,0,255)' },
        { color: 'rgb(127,0,255)' },
        { color: 'rgb(255,0,255)' },
        { color: 'rgb(255,0,127)' },
        { color: 'rgb(255,0,0)' },
      ],
    })
    
    e.target.onmouseleave = stopAnimation
    e.target.ontouchleave = stopAnimation
    
    function stopAnimation () {
      setTimeout(() => {
        rainbowAnimation.pause()
        anime({
          duration: 1000,
          targets: [e.target],
          color: 'rgb(255,255,255)',
        })
      }, 500)
    }
  }
</script>

<template>
  <div class="rainbow" v-for="(letter, i) in letters" @mouseover="startAnimation" @touchmove="startAnimation" :key="i">{{ letter }}</div>
</template>

<style scoped lang="scss">
  .rainbow {
    display: inline;
  }
</style>