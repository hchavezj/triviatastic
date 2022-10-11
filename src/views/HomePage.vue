<script setup></script>

<template>
  <div class="brand">
    <img class="logo" src="logo.svg" alt="logo" />
    <h1 class="title">Triviantastic</h1>
    <img class="logo" src="logo.svg" alt="logo" />
  </div>
  <div class="categories">
    <RouterLink v-for="n in 24" :key="n" :to="`/question/category/${n}`" class="category"
      >Categories - {{ n }}</RouterLink
    >
  </div>
</template>

<style lang="postcss" scoped>
.brand {
  @apply flex items-center justify-center gap-4;

  & .logo {
    @apply h-16 w-16;
  }
  & .title {
    @apply text-6xl font-thin uppercase tracking-widest text-slate-200;
  }
}

.categories {
  @apply grid flex-grow grid-cols-4 gap-4;

  & .category {
    @apply flex h-32 w-40 items-center justify-center rounded-lg border-4 border-slate-900 py-4 text-center font-bold uppercase transition-colors duration-300;

    &:hover {
      @apply cursor-pointer bg-slate-900;
    }
  }
}
</style>
