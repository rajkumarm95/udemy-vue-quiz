<script setup>
const props  = defineProps(['questionStatus','barPercentage'])
</script>

<template>
    <div>
        <header>
            <h4>Questions {{ props.questionStatus }}</h4>
            <div class="bar">
                <div class="completion" :style="{width:props.barPercentage}"></div>
            </div>
        </header>
    </div>
</template>

<style scoped>
header {
    margin-top: 20px;

}

header h4 {
    font-size: 30px;
}

.bar {
    width: 300px;
    height: 50px;
    border: 3px solid maroon;
}

.completion {
    height: 100%;
    width: 66%;
    background-color: bisque;
}
</style>