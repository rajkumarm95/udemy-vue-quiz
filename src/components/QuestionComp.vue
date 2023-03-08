<script setup>
import { defineProps, defineEmits } from 'vue'; // import defineEmits from vue
const emit = defineEmits(["selectOption"]); // define the name of the event
const emitSelectedOption = (isCorrect)=>{
    emit("selectOption", isCorrect) // emit the event with the name and the value
}
const props = defineProps(['question']);
</script>

<template>
    <div>
        <div class="question-container">
            <h1 class="container">
                {{ props.question.text }}
            </h1>
        </div>
        <div class="answers-container">
            <div v-for="option in question.options" :key="option.id"
            @click="emitSelectedOption(option.isCorrect)" class="option">
                <p class="option-label">{{ option.label }}</p>
                <div class="option-value">
                    <p>{{ option.text }}</p>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.question-container {
    margin-top: 20px;
}

.question {
    font-size: 40px;
    margin-bottom: 20px;
}

.option {
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
}

.option-label {
    background-color: bisque;
    width: 50px;
    height: 50px;
    font-size: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.option-value {
    background-color: rgb(255, 243, 229);
    width: 100%;
    font-size: 30px;
    padding: 0 20px;

}
</style>