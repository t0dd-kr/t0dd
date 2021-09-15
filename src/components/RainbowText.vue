<script setup lang="ts">
  import RainbowLetter from '@/components/RainbowLetter.vue'

  const props = defineProps({
    letters: null
  })
</script>

<template>
  <RainbowLetter v-for="(letter, i) in letters" :key="i" :letter="letter"/>
</template>

<style scoped lang="scss">

</style>