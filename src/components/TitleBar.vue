<script setup></script>

<template>
  <div class="brand">
    <img src="/logo.svg" alt="logo" class="h-16 w-16" />
    <h1 class="title">
      <slot />
    </h1>
    <img src="/logo.svg" alt="logo" class="h-16 w-16" />
  </div>
</template>

<style lang="postcss" scoped>
.brand {
  @apply flex m-0 items-center justify-center gap-4 pt-5 pb-5;

  & .title {
    @apply text-6xl font-thin uppercase tracking-widest text-slate-200;
  }
}
</style>
