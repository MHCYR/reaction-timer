<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">PLAY</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2222 + Math.random() * 4444;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
body {
  background-color: #27272b;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: white;
  margin-top: 60px;
}

button {
  color: white;
  background: rgb(100, 71, 206);
  background: linear-gradient(
    90deg,
    rgba(100, 71, 206, 1) 0%,
    rgba(63, 94, 251, 1) 100%
  );
  padding: 20px 50px;
  border: none;
  border-radius: 100px;
  font-size: 1.3rem;
  text-align: center;
  letter-spacing: 4px;
  cursor: pointer;
}

button[disabled] {
  cursor: not-allowed;
  background: rgb(55, 53, 59);
  opacity: 0.3;
}
</style>
