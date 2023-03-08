<script setup>
import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';
const props = defineProps(['total', 'correctAns']);
</script>

<template>
    <div class="result">
        <p>your Results</p>
        <h1>
            {{ props.correctAns }} / {{ props.total }}
        </h1>
        <RouterLink to="/">Back to Home</RouterLink>
    </div>
</template>


<style scoped>
.result {
    text-align: center;
    padding: 100px 0;
}

p {
    font-size: 25px;

}

h1 {
    font-size: 80px;
}
</style>