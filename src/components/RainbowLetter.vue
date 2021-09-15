<script setup lang="ts">
  import anime from 'animejs';
  import type { AnimeInstance } from 'animejs';
  import { useMouse } from '@vueuse/core'
  import { useMouseInElement } from '@vueuse/core'
  import { ref, watch, onMounted } from 'vue'

  const props = defineProps({
    letter: null
  })

  const target = ref(null)
  const { x: mouseX, y: mouseY } = useMouse()
  const { isOutside } = useMouseInElement(target)

  watch(isOutside, isOutside => {
    if (isOutside) {
      setTimeout(() => {
        rainbowAnimation?.pause()
        resetAnimation?.play()
      }, 500)
    } else {
      rainbowAnimation?.play()
    }
  })

  let rainbowAnimation :AnimeInstance, resetAnimation :AnimeInstance;

  onMounted(() => {
    rainbowAnimation = anime({
      targets: [target.value],
      duration: 1000,
      loop: true,
      autoplay: false,
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


    resetAnimation = anime({
      duration: 1000,
      targets: [target.value],
      color: 'rgb(255,255,255)',
      autoplay: false,
    })
  })

</script>

<template>
  <div class="rainbow" ref="target">{{ letter }}</div>
</template>

<style scoped lang="scss">
  .rainbow {
    display: inline;
  }
</style>