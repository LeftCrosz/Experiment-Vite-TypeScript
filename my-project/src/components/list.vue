<script setup lang="ts">
import { ref } from 'vue';

const newItem = ref('');
const items = ref<string[]>([]);

function addItem() {
if(newItem.value.trim() == '') {
  alert("Please type something");
  return;
}

  items.value.push(newItem.value);
  newItem.value = '';
}

</script>

<template>
  <h1 class="mt-30 text-green-500 text-[60px] font-bold text-center">To-do List</h1>

  <section class="flex flex-col justify-center items-center">
    <div class="flex flex-row justify-center items-center">
      <input v-model="newItem" class="text-center border text-amber-50 bg-gray-600 text-[20px] rounded-2xl max-w-3rem" type="text" placeholder="Enter your list here">
      
      <button type="submit" v-on:click="addItem()" class="ml-2 font-bold border w-18 rounded cursor-pointer bg-gray-600 text-amber-50 hover:bg-white hover:text-black">Add</button>
    </div>

    <div>
      <ul class="text-[20px]">Item list here:</ul>
      <li v-for="(item, i) in items" :key="i">{{ item }}</li>
    </div>
  </section>

  
</template>