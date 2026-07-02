<script setup lang="ts">
import { ref } from 'vue'

const isOpen = ref(false)

function toggle() {
  if(isOpen.value) {
    isOpen.value = false;
  } else {
    isOpen.value = true;
  }
}
</script>


<template>
  <h1 class="text-green-500 text-[60px] font-bold text-center">FAQ</h1>
  
  <section>
    <div class="border rounded-sm ml-10 mr-10 p-2 bg-gray-700 font-bold text-white">
      <p v-on:click="toggle">Question 1</p>
      <p id="ans-1" class="overflow-hidden transition-all duration-200 ease-in-out" :class="{ 'max-h-40' : isOpen, 'max-h-0': !isOpen }">Answer 1</p>
    </div>
  </section>
</template>
