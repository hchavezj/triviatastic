<script setup></script>

<template>
  <div class="brand">
    <slot name="logo" />
    <h1 class="title">
      <slot />
    </h1>
    <slot name="logo" />
  </div>
</template>

<style lang="postcss" scoped>
.brand {
  @apply m-0 flex items-center justify-center gap-4 pt-5 pb-5;

  & :slotted(img) {
    @apply h-16 w-16;
  }
  & .title {
    @apply text-6xl font-thin uppercase tracking-widest text-slate-200;
  }
}
</style>
