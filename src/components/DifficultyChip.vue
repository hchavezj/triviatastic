<script setup>
const props = defineProps({
  difficulty: {
    type: String,
    default: '',
    require: true,
  },
})
</script>

<template>
  <p
    class="difficulty"
    :class="
      props.difficulty === 'easy' ? 'bg-green-700' : props.difficulty === 'medium' ? 'bg-yellow-600' : 'bg-red-700'
    "
  >
    {{ props.difficulty }}
  </p>
</template>

<style lang="postcss" scoped>
.difficulty {
  @apply fixed bottom-8 left-8 rounded-full px-4 py-2 text-2xl font-bold capitalize;
  color: #dcd7ba;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.537), -2px -2px 4px rgba(255, 255, 255, 0.071);
  box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);
}
</style>
