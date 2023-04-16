<template>
  <h1> Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <BlockGame v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResult" :score="score"/>
  </template>

<script>
import BlockGame from './components/Block.vue';
import Result from './components/Result.vue';
export default {
  name: "App",
  components: {
    BlockGame,Result
  },
  data() {
    return {
     isPlaying: false,
     delay: null,
     score: null,
     showResult: false
    }
  },
  methods: {
    start() {
      this.showResult = false;
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      console.log("the game started after " + this.delay + "ms");
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      console.log("the game ended after " + reactionTime + "ms");
      this.showResult = true;
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
