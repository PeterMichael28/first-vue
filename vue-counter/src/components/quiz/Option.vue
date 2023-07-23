<script setup>
import {defineProps} from 'vue'

const props = defineProps(['option'])
const emit = defineEmits(['selectedOption'])

const emitSelected = (isCorrect) => {
    emit('selectedOption', isCorrect)
}


</script>


<template>
    <div class="option" @click="emitSelected(props.option.isCorrect)">
                    <p class="option-label">{{ props.option.label }}</p>
                    <div class="option-value">
                        <p>{{ props.option.text }}</p>
                    </div>
                   
                </div>
</template>

<style scoped>
.option{
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
    
}

.option-label {
    background-color: orange;
    width: 50px;
    height: 50px;
    font-size: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
}

.option-value {
    background-color: rgb(170, 168, 168);
    width: 100%;
    font-size: 30px;
    padding: 0 20px;
    display: flex;
    align-items: center;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
}
</style>