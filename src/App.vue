<template>
  <h1>Reaction Timer</h1>
  <h3 class="info">Total score: <span class="big-numbers">{{ totalScore }}</span></h3>
  <button @click="start" :disabled="isPlaying">START</button>
  <button @click="clear">RESET</button>
  <p v-if="delay !=null">
        <small>
            Квадратик появится через: {{ delay }} милисекунд!
        </small>
  </p>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" /> 
  <Results v-if="showResults" :score="score" />

</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results'

export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      totalScore: 0
    }
  },
  methods: {
    start(){
      this.delay = Math.round(2000 + Math.random() * 4000)
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
      this.totalScore += this.score
    },
    clear() {
      this.showResults = false
      this.score = null
      this.isPlaying = false
      this.delay = null
      this.total.score = 0
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
.info {
  color: rgb(31, 121, 148)
}
button {
   min-width: 200px;
   background: #0faf87;
   color: white;
   border: none;
   border-radius: 5px;
   padding: 9px 16px;
   font-size: 16px;
   letter-spacing: 1px;
   cursor: pointer;
   margin-right: 5px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
.big-numbers {
  font-size: 46px;
}
</style>
