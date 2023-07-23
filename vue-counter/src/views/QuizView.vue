<script setup>
import { useRoute } from 'vue-router'
import { ref, computed } from 'vue'
import q from '../data/quiz.json'
import Question from '../components/quiz/Question.vue'
import Option from '../components/quiz/Option.vue'


const route = useRoute()

const quiz = q.find((qui) => qui.id === parseInt(route.params.id))

let currentQuestion = ref(0)
let correctAnswer = ref(0)

const questionCompletedStatus = computed( () => (( currentQuestion.value + 1 ) / quiz.questions.length ) * 100 + '%')

const onOptionSelected = (isCorrect) => {
    if ( isCorrect ) {
    correctAnswer.value++
   }

   currentQuestion.value++
}
</script>
 
<template>
  <div>
    <header>
      <h4>Question {{ currentQuestion + 1 }}/{{ quiz.questions.length }}</h4>
      {{ correctAnswer }}
      <div class="bar">
        <div class="completion" :style="{width: questionCompletedStatus}"></div>
      </div>
    </header>

    <div>
      <Question :question="quiz.questions[currentQuestion].text" />
      <div class="answers-con">
        <!-- answer options -->
        <Option
          v-for="option in quiz.questions[currentQuestion].options"
          :key="option.id"
          :option="option"
          @selectedOption="onOptionSelected"
        />
      </div>
    </div>

    
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
  height: 40px;
  border: 2px solid orange;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: orange;
}
</style>
