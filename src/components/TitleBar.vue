<script setup></script>

<template>
  <div class="brand">
    <img class="logo" src="logo.svg" alt="logo" />
    <h1 class="title">Triviantastic</h1>
    <img class="logo" src="logo.svg" alt="logo" />
  </div>
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
</style>
