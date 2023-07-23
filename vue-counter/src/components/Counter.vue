<script setup>
import {ref} from 'vue'

const count = ref(0)

</script>


<template>
 <main>
  <div class="con">  
    <h4>
      the current count is ...
    </h4>
    <h1>{{count}}</h1>

    <div>
      <bUtton @click="count++">
        +
      </bUtton>
      <bUtton @click="count--">
        -
      </bUtton>
    </div>
  </div>

  
 </main>
</template>


<style scoped>
 main {
  background-color: gray;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  text-align: center
 }

 h1{
  font-size: 65px;
  font-weight: bold;
  
 }

 button{
  margin: 10px;
  padding: 10px 20px;
  font-size: 35px;
  cursor: pointer;
 }
</style>