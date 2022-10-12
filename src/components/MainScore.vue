<script setup>
import useScore from '@/composables/useScore'

const { score } = useScore()
</script>
<template>
  <p class="score">Score: {{ score }}</p>
</template>

<style lang="postcss" scoped>
.score {
  @apply fixed bottom-8 right-8 rounded-full px-4 py-2 text-2xl font-bold uppercase;
  color: #dcd7ba;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.537), -2px -2px 4px rgba(255, 255, 255, 0.071);
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);
}
</style>
