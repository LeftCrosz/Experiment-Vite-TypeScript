<script setup lang="ts">
import { ref } from 'vue';


const newItem = ref('');
const itemList = ref<string[]>([])

function addItem() {
    if(newItem.value.trim() !== "") {
        itemList.value.push(newItem.value)
        newItem.value = " "
    }
}


</script>

<template>
    <h1 class="text-[40px] font-bold text-center">To-do List</h1>
    
    <div class="text-2xl text-center">
        <input v-model="newItem" @keyup.enter="addItem" type="text" placeholder="Type something here" class="rounded p-0.5 border">
        <button @click="addItem()" class="bg-gray-800 text-white p-2  rounded-2xl m-2 cursor-pointer">Add to List</button>
        <ul class="font-bold">Your Added List here:
        </ul>
        <p v-for="(item, index) in itemList" :key="index">{{ item }}</p>
    </div>
</template>