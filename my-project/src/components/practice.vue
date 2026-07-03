<script setup lang="ts">
import { ref } from "vue"
import qna_json from "../data/questions.json"

interface qnaItems {
    question: string;
    answer: string;
    open: boolean;
}

const qnaList = ref<qnaItems[]>(qna_json);

function toggleQna(qna: qnaItems) {
    qna.open = !qna.open;
}

</script>

<template>
    <h1 class="text-center text-[50px] font-bold">QnA</h1>
    <div v-for="(qna, index) in qnaList" :key="index" v-on:click="toggleQna(qna)" class="flex flex-col justify-center items-center select-none cursor-pointer">
        <div class="text-[20px] font-bold min-w-100 p-3 max-w-100 border-gray-200 border" :class="{'bg-gray-400 text-black': index%2==0, 'bg-gray-700 text-zinc-200' : index%2!==0}">
            <div class="flex justify-between items-center">
            <p>{{ qna.question }}</p>

            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6" :class="{'hidden' : qna.open, 'max-h-20 opacity-100' : !qna.open}">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v6m3-3H9m12 0a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
            </svg>

            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="size-6" :class="{'max-h-20 opacity-100' : qna.open, 'hidden' : !qna.open}">
            <path stroke-linecap="round" stroke-linejoin="round" d="M15 12H9m12 0a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z" />
            </svg>


            </div>
                <p class="overflow-hidden transition-all ease-in-out duration-200" :class="{'max-h-20 opacity-100' : qna.open, 'max-h-0 opacity-0' : !qna.open}">{{ qna.answer }}</p>
        </div>

    </div>

</template>