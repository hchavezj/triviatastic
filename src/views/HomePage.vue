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
