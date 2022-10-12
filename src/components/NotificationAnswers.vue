<script setup>
const props = defineProps({
  correct: {
    type: Boolean,
    require: true,
  },
})
</script>

<template>
  <div class="notification" :class="props.correct ? 'bg-green-600' : 'bg-red-600'">
    {{ props.correct ? 'Corret' : 'Wrong' }}
  </div>
</template>

<style lang="postcss" scoped>
.notification {
  @apply absolute inset-0 flex items-center justify-center px-4 py-2 text-8xl font-bold uppercase tracking-widest;
  color: #dcd7ba;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.537), -2px -2px 4px rgba(255, 255, 255, 0.071);
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);
}
</style>
