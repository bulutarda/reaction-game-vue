<template>
  <h1>Reaction Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResult" :result="result"/>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data(){
    return{
      isPlaying: false,
      delay: null,
      result: 0,
      showResult: false,
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000 //7000-2000 
      this.isPlaying = true
      this.showResult = false

    },
    endGame(reactionResult){
      this.result = reactionResult
      this.isPlaying = false
      this.showResult = true
    }
  }
};
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
