<template>
  <p class="btn dotted thick">
    Rection Time - {{ score }} ms
    <br />
    <span class="rank">{{ rank }}</span>
  </p>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Fast Reaction Time";
    } else if (this.score < 400) {
      this.rank = "Decent Reaction Time";
    } else {
      this.rank = "Slow Reaction Time";
    }
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/scss/_variables.scss";

.rank {
  font-size: 2rem;
  color: $gray;
  font-weight: bold;
}

.btn {
  align-self: center;
  background: transparent;
  padding: 1rem 1rem;
  transition: all 0.5s ease;
  color: $gray;
  font-size: 2rem;
  letter-spacing: 1px;
  outline: none;
  box-shadow: 20px 38px 34px -26px hsla(0, 0%, 0%, 0.2);
  border-radius: 255px 15px 225px 15px/15px 225px 15px 255px;

  &.dotted.thick {
    border: dotted 7px #41403e;
  }
}

p {
  font-size: 2.5rem;
  color: $gray;
  margin: 4rem auto;
  max-width: 30rem;
}
</style>
