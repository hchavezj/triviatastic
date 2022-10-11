<script setup>
import TitleBar from '@/components/TitleBar.vue'
import MainScore from '@/components/MainScore.vue'
</script>

<template>
  <TitleBar>
    <template #logo>
      <img src="logo.svg" alt="logo" />
    </template>
    Triviatastic
  </TitleBar>
  <main>
    <div class="card">
      <RouterView />
    </div>
  </main>
  <MainScore />
</template>

<style lang="postcss" scoped>
.brand {
  @apply m-0 flex items-center justify-center gap-4 pt-5 pb-5;

  & .logo {
    @apply h-16 w-16;
  }
  & .title {
    @apply text-6xl font-thin uppercase tracking-widest text-slate-200;
  }
}
main {
  @apply flex h-5/6 items-center justify-center;
  & .card {
    @apply flex w-11/12 flex-col items-center gap-16 overflow-auto rounded-lg bg-slate-600 p-8 text-slate-200 shadow-lg;
  }
}
</style>
