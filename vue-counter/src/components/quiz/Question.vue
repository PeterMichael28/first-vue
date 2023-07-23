<script setup>
import {defineProps} from 'vue'

// eslint-disable-next-line vue/no-setup-props-destructure
const {question} = defineProps(['question'])


</script>

<template>
    <div class="question-con">
                <h1 class="question">
                    {{question}}
                </h1>
            </div>
</template>

<style scoped>
.question-con {
    margin-top: 20px;
}

.question {
    font-size: 35px;
    margin-bottom: 20px;
}
</style>