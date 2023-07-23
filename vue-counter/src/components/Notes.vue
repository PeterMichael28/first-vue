<script setup>
import {ref} from "vue"
const showModal = ref(false) // toggle modal visibility with this variable

const newNote = ref("")
const errorMsg = ref("")

const notes = ref([])

const handleAddNotes = () => {
  if ( newNote.value !== "" &&  newNote.value.length > 7) { 
    notes.value.push( {
      text: newNote.value,
      dateAdded: new Date(),
      id: Math.floor( Math.random() * 1000000 ),
      backgroundColor: '#' + (0x1000000 + Math.random() * 0xFFFFFF).toString(16).substr(1,6)
    })
    showModal.value = false
    errorMsg.value = ''
    newNote.value = ""
  } else {
    errorMsg.value = 'Notes has to be at least 7 characters or more'
    return
  }
}

const handleDelete = ( id ) => {
  const filteredNotes = notes.value.filter(note => note.id !== id)

  return notes.value = filteredNotes
}



</script>


<template>
 <main>
  <div class="cont">
    <!-- content goes here -->
    <header>
      <h1>Notes</h1>
      <button @click="showModal = true">+</button>
    </header>

    <div class="cards-con">
      <div v-for="item in notes" class="card" :key="item.id" :style="{backgroundColor: item.backgroundColor}">
        
        <p class="main-text">{{item.text}}</p>
        <div class="del">
          <p class="date">2{{item.dateAdded.toLocaleDateString('en-US')}}</p>
          <button @click="handleDelete(item.id)">delete</button>
        </div>
      </div>
    </div>
  </div>

  <div v-if="showModal" class="overlay">
    <div class="modal">
      <p v-if="errorMsg" class="error">{{ errorMsg }}</p>
      <textarea name="notes" id="notes" cols="30" rows="8" v-model="newNote"></textarea>
      <button class="add" @click="handleAddNotes" >Add Notes</button>
      <button  @click="showModal = false" class="close">X</button>
    </div>
  </div>
  
 </main>
</template>


<style scoped>
main{
  height: 100vh;
  width: 100vw;

}

.cont {
max-width: 1000px;
padding: 10px;
margin: 0 auto;
}

header {
display: flex;
justify-content: space-between;
align-items: center;
}

h1{
  font-weight: bold;
  margin-bottom: 25px;
  font-size: 55px;
}

header button {
  border: none;
  padding: 10px;
  width: 50px;
  height: 50px;
  cursor: pointer;
  background: rgb(21, 20, 20);
  border-radius: 100%;
  color: white;
  font-size: 25px;
}

.card {
  width: 225px;
  height: 225px;
  background-color: rgb(237, 182, 44);
  padding: 10px;
  border-radius: 15px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-right: 20px;
  margin-bottom: 20px;
}

.main-text {

}

.date{
  font-size: 12px;
  font-weight: bold;
}

.cards-con {
  display: flex;
  flex-wrap: wrap;

}

.overlay {
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, .5);
  z-index: 10;
  display: flex;
  align-items: center;
  justify-content: center;
}

.modal {
  width: 350px;
  background-color: white;
  border-radius: 10px;
  padding: 30px;
  position: relative;
  display: flex;
  flex-direction: column;
}

.modal .add {
  padding: 10px 20px;
  font-size: 20px;
  width: 100%;
  background-color: blueviolet;
  color: white;
  cursor: pointer;
  margin-top: 15px;
  border: none;
  outline: none;
}

.close {
  position: absolute;
  top: 10px;
  right: 10px;
  background-color: rgb(78, 7, 7);
  width: 30px;
  height: 30px;
  border-radius: 100%;
  color: white;
  font-weight: bold;
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  outline: none;
  cursor: pointer;
  
}

textarea{
  padding: 10px;
  outline: none;
  border: 1px solid gray;
}

.error{
  color: red;
  font-size: 15px;
  margin-bottom: 3px;
}

.del {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.del button {
  padding: 10px 20px;
  background: white;
  color: red;
  border: none;
  outline: none;
  cursor: pointer;
  border-radius: 20px;

}
</style>