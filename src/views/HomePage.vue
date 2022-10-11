<script setup>
import { onMounted, ref } from 'vue'
import useAPI from '@/composables/useAPI'
const api = useAPI()
const categories = ref([])
onMounted(async () => {
  categories.value = await api.getCategories()
})
</script>

<template>
  <div class="brand">
    <img class="logo" src="logo.svg" alt="logo" />
    <h1 class="title">Triviantastic</h1>
    <img class="logo" src="logo.svg" alt="logo" />
  </div>
  <div class="categories">
    <RouterLink
      v-for="category in categories"
      :key="category.id"
      :to="`/question/category/${category.id}`"
      class="category"
    >
      {{ category.name }}</RouterLink
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
    @apply flex h-32 items-center justify-center rounded-lg border-4 border-slate-900 p-4 text-center font-bold uppercase transition-colors duration-300;

    &:hover {
      @apply cursor-pointer bg-slate-900;
    }
  }
}
</style>
