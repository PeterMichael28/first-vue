<script setup>
import q from '../data/quiz.json'
import { ref, watch } from 'vue';
import Card from '../components/quiz/Card.vue'

const quizzes = ref(q)
let searchString = ref('')


watch( searchString, () => {
 
    quizzes.value = q.filter(quiz => quiz.name.toLowerCase().includes(searchString.value.toLowerCase()))

})
</script>

<template>
  <div>
    <header>
      <h1>Quizzes</h1>
      <input type="text" v-model.trim="searchString" placeholder="Search...">
    </header>

    <div class="options-container">
     
      <Card v-for="quiz in quizzes" :key="quiz.id" :quiz="quiz"/>
    
    </div>
  </div>
</template>

<style scoped>

  header{
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;

  }

  header h1 {
    font-weight: bold;
    margin-right: 30px;

  }

  header input {
    border: none;
    background-color: rgba(128, 128, 128, .1);
    padding: 10px;
    border-radius: 5px;
  }


  .options-container {
    display: flex;
    flex-wrap: wrap;
    margin-top: 40px;
  }

 
</style>