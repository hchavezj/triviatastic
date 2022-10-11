<script setup>
import MainScore from '@/components/MainScore.vue'
</script>

<template>
  <main>
    <div class="card">
      <RouterView />
    </div>
  </main>
  <MainScore />
</template>

<style lang="postcss" scoped>
:root {
  --sumi-ink: #1f1f28;
  --fuji-white: #dcd7ba;
  --carp-yellow: #e6c384;
  --wave-read: #e46876;
  --surimi-orange: #ffa066;
  --neu-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);
}
main {
  @apply flex h-screen items-center justify-center bg-gradient-to-b from-gray-900 to-gray-600 text-slate-200;
  & .card {
    @apply flex h-5/6 min-h-fit w-11/12 flex-col items-center gap-16 overflow-auto rounded-lg p-8;
    background-color: var(--sumi-ink);
    color: var(--fuji-white);
    border-radius: 8px;
    box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);
  }
}
</style>
