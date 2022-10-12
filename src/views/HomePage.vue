<script setup>
import { onMounted, ref } from 'vue'
import useAPI from '@/composables/useAPI'
import TitleBar from '@/components/TitleBar.vue'

const { categories, getCategories } = useAPI()

onMounted(async () => {
  await getCategories()
})
</script>

<template>
  <TitleBar>Triviantastic</TitleBar>
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
    @apply flex h-32 items-center justify-center rounded-lg p-4 text-center font-bold uppercase transition-colors duration-300;
    box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.537), -4px -4px 8px rgba(255, 255, 255, 0.071);

    &:hover {
      @apply cursor-pointer;
      box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.537), inset -2px -2px 2px rgba(255, 255, 255, 0.071);
    }
  }
}
</style>
