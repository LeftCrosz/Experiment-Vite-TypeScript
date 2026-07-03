<script setup lang="ts">
import { ref } from 'vue'

const faqs = ref([
  { question: 'Question 1', answer: 'Answer 1 long answer ok?', open: false},
  { question: 'Question 2', answer: 'Answer 2 short answer', open: false},
]);

function toggle(faq: { open: boolean; }) {
  faq.open = !faq.open;
};
</script>


<template>
  <h1 class="text-green-500 text-[60px] font-bold text-center">FAQ</h1>
  <div class="flex flex-col justify-center items-center max-w-full">
    <div v-for="(faq, index) in faqs" :key="index" v-on:click="toggle(faq)" class="min-w-80 max-w-80 border rounded-sm p-2 bg-gray-700 text-[30px] font-bold text-white cursor-pointer select-none">

      <p class="text-center">{{ faq.question }}</p>
      <p class="overflow-hidden transition-all duration-500 ease-in-out opacity-0 text-green-300 pl-2 pr-2" :class="{ 'max-h-40 opacity-100' : faq.open, 'max-h-0 opacity-0' : !faq.open }">{{ faq.answer }}</p>
    </div>
  </div>
</template>
