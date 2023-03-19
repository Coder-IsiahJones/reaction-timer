<template>
  <h1>Reaction Timer</h1>
  <button class="btn lined thick" @click="start()" :disabled="isPlaying">
    play
  </button>
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
      this.delay = 2000 + Math.random() * 5000;
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

<style lang="scss">
@import url(https://fonts.googleapis.com/css?family=Patrick+Hand+SC);
@import "./assets/scss/_variables.scss";

* {
  font-family: "Patrick Hand SC", cursive;
  background: $backgournd;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;

  h1 {
    font-size: 4rem;
    color: $gray;
  }
}

.btn {
  align-self: center;
  background: transparent;
  padding: 1rem 1rem;
  margin: 0 1rem;
  transition: all 0.5s ease;
  color: $gray;
  font-size: 2rem;
  letter-spacing: 1px;
  outline: none;
  box-shadow: 20px 38px 34px -26px hsla(0, 0%, 0%, 0.2);
  border-radius: 255px 15px 225px 15px/15px 225px 15px 255px;

  &:hover {
    box-shadow: 2px 8px 4px -6px hsla(0, 0%, 0%, 0.3);
  }
  &.lined.thick {
    border: solid 7px $gray;
  }
  &.dotted.thick {
    border: dotted 5px $gray;
  }
  &.dashed.thick {
    border: dashed 5px $gray;
  }
  &.lined.thin {
    border: solid 2px $gray;
  }
  &.dotted.thin {
    border: dotted 2px $gray;
  }
  &.dashed.thin {
    border: dashed 2px $gray;
  }
  &:disabled {
    opacity: 0.2;
    cursor: not-allowed;
  }
}
</style>
