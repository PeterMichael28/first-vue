<script setup>
    import { defineProps } from 'vue';
import { RouterLink } from 'vue-router';
    
    const props = defineProps(['quiz'])

 
</script>


<template>
      <RouterLink class="card" :to="`/quiz/${props.quiz.id}`">
        <img :src="props.quiz.img" alt="">

        <div class="card-text">
          <h2>{{props.quiz.name}}</h2>
          <p>{{props.quiz.questions.length}} Questions</p>
        </div>
      </RouterLink>
</template>

<style scoped>

.card {
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, .1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
    text-decoration: none;
    color: black;
  }

  .card img {
    width: 100%;
    height: 190px;
    margin: 0;
  }

  .card-text{
    padding: 0px 10px 5px;
  }

  .card-text h2{
    font-weight: bold;
  }


</style>