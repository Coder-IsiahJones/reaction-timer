<template>
  <p>Rection Time - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
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

<style scoped>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
