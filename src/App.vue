<template>
<h1 :class="lol">{{ persons[0].name }}</h1>
<button @click="showText">Click me</button>
<input type="text" ref="name">

<div>
  <ul>
    <li v-for="person in persons">
      <span>Name: {{ person.name }}</span>
      <br>
      <span>Age: {{person.age}}</span>
    </li>
  </ul>
</div>

<button @click="toggleModal">Close Modal</button>

<div v-if="modal">
<Alert :header="persons[1].name" :footer="msg" @close="toggleModal">
  
      <h1>Slot</h1>
      <span>Alert</span>
      <h1 class="default" :class="{prop: prop == true}">This is a slot</h1>
      
      <template v-slot:links>
        <a href="#">Sign Up</a>
        <a href="#">More</a>
      </template>
      
</Alert>

</div>

<div class="modal-two" v-if="modal2">
  <Alert @close="toggleModal2">
    <input type="text" placeholder="name">
    <input type="number" placeholder="age">
    <template v-slot:links>
        <a href="#">Sign Up</a>
        <a href="#">More</a>
    </template>
  </Alert>
</div>
  <button @click="toggleModal2">Toggle  Another Modal</button>
  
<br>
<br>

<h1>Reaction timer</h1>
<button :disabled="isPlaying" @click="startPlaying">Start</button>

<Block @end="endGame" :delay="delay" v-if="isPlaying"></Block>

<Result v-if="showResult" :result="score"></Result>

</template>

<script>
import Alert from './components/Alert.vue'
import Block from './components/Block.vue'
import Result from './components/Result.vue'

export default {
  name: 'App',
  data() {
    return{
    lol: 'vovo',
    persons: [
      {name : 'John', age : 21},
      {
        name : 'Vir', age : 17}
        ],
    msg: 'I am a prop',
    modal: false,
    modal2: false,
    delay: null,
    isPlaying: false,
    score: null,
    showResult: false
    }
  },
  
  methods: {
    showAlert(){
      alert(this.persons[0].name)
    },
    showText(){
      alert(this.$refs.name.value)
    },
    toggleModal(){
      this.modal = !this.modal
    }, 
    toggleModal2(){
      this.modal2 = !this.modal2
    },
    
    
    startPlaying(){
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResult = false
    },
    endGame(time){
      this.isPlaying = false
      this.score = time
      this.showResult = true
    }
  },
  components: {
    Alert,
    Block,
    Result
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
