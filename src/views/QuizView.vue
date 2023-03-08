<script setup>
import { computed, ref/* , watch */ } from 'vue';
import Questions from '../components/QuestionComp.vue';
import QuestionHeader from '../components/QuizHeader.vue';
import quizes from '../data/quizes.json';
import Results from '../components/ResultComp.vue';
import { useRoute } from 'vue-router';
const route = useRoute();
const quizId = parseInt(route.params.id);
const currentQuestionIndex = ref(0);
const quiz = quizes.find(q => q.id === quizId);
// const questionStatus = ref(`${ currentQuestionIndex.value }/${ quiz.questions.length }`)

// watch(()=> currentQuestionIndex.value, ()=>{
// questionStatus.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
// })


const questionStatus = computed(() => `${ currentQuestionIndex.value }/${ quiz.questions.length }`);
const barPercentage = computed(() => `${ currentQuestionIndex.value / quiz.questions.length * 100 }%`);
const noOfCurrentAns = ref(0);
const onOptionSelected = (isCorrect) => {
    if (isCorrect) {
        noOfCurrentAns.value++;
    }
    if(quiz.questions.length -1 === currentQuestionIndex.value){
        showResults.value = true
    }
    currentQuestionIndex.value++;
};

const showResults = ref(false)
</script>

<template>
    <div>
        <QuestionHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />
        <div>
            <Questions v-if="!showResults" :question="quiz.questions[currentQuestionIndex]" @selectOption="onOptionSelected" />
            <Results v-else :total="quiz.questions.length" :correctAns="noOfCurrentAns" />
        </div>
    </div>
</template>