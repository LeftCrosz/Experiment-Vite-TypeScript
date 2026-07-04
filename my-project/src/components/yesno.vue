<script setup lang="ts">
import { ref, watch } from "vue";

const question = ref('');
const answer = ref('Qustion must contain a question mark <3')
const loading = ref(false)


watch(question, async(newQuestion, oldQuestion) => {
    if(newQuestion.includes("?")) {
        loading.value = true
        answer.value = "Thinking"
        try {
            const res = await fetch("https://yesno.wtf/api")
            answer.value = (await res.json()).answer
        } catch (error) {
            answer.value = "Error! Can't fetch the answer!"
        } finally {
            loading.value = false
        }
    }
})



</script>

<template>
<p>Ask a yes/no question:
    <input v-model="question" :disabled="loading" class="border" type="text">
</p><br>
<p>Answer:</p>
<p class="font-bold">{{ answer }}</p>
</template>




