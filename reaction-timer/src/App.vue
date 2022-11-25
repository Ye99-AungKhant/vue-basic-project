<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Start</button>
  <Block v-if="isPlaying" :delaytime="delay" @end="endGame"/>

  <Results v-if="showResult" :score="score"/>
  <!-- <p v-if="showResult">Reaction Time : {{score}} ms</p> -->
</template>

<script>

import Block from './components/Block'
import Results from './components/Results'

export default {
  name: 'App',
  components: {
   Block, Results
  },
  data(){
    return{
      isPlaying: false,
      delay: null,
      score:null,
      showResult:false
    }
  },
  methods:{
    start(){
      this.isPlaying = true,
      this.delay = 2000 + Math.random() * 5000
      this.showResult = false
      console.log(this.delay)
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying =false
      this.showResult =true
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
