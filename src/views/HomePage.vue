<script setup>
import { onMounted, ref } from 'vue'
import BaseTitle from '@/components/BaseTitle.vue';
import useAPI from '@/composables/useAPI'
import MainScore from '@/components/MainScore.vue';

const { categories, getCategories } = useAPI()

onMounted(async () => {
  await getCategories()
})


</script>

<template>
  <BaseTitle>TRIVIA APPLICATION - <MainScore></MainScore></BaseTitle>
  <div class="grid flex-grow grid-cols-4 gap-12 m-20">
      <RouterLink v-for="category in categories" 
      :key="category.id"
      :to="`/question/category/${category.id}`"
      class="bg-white text-center flex h-32 items-center justify-center rounded-lg border-4 border-slate-300 py-4 font-bold uppercase hover:cursor-pinter hover:border-black hover:bg-pink-300 hover:text-white transition-colors duration-250"
      >
        {{ category.name }}
      </RouterLink>
  </div>

  
</template>
