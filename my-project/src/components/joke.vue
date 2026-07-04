<script setup lang="ts">
import { ref, watch } from 'vue';

const joke = ref('Want funny joke click the button');
const loading = ref(false);

const generateJoke = async() => {
        loading.value = true;
        joke.value = "Thinking..."
        try {
            const res = await fetch("https://api.chucknorris.io/jokes/random")
            joke.value = (await res.json()).value;
        } catch (err) {
            joke.value = "Error generating joke: " + err
        } finally {
            loading.value = false;
        }
}

</script>



<template>
<h1 class="font-bold text-center">Random Jokes</h1>
<div class="flex flex-col justify-center items-center">
    <button v-on:click="generateJoke" class="border p-0.5 rounded-4xl hover:bg-gray-200 cursor-pointer text-[8px]" :disabled="loading">Generate Joke</button>
    <p class="text-[10px] max-w-50 text-center">{{ joke }}</p>
</div>

</template>