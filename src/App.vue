<script setup></script>

<template>
  <div class="brand">
    <img class="logo" src="logo.svg" alt="logo" />
    <h1 class="title">Triviantastic</h1>
    <img class="logo" src="logo.svg" alt="logo" />
  </div>
  <main>
    <div class="card">
      <RouterView />
    </div>
  </main>
  <p class="score">Score: 100</p>
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

.score {
  @apply fixed bottom-8 right-8 text-2xl font-bold uppercase;
}
</style>
