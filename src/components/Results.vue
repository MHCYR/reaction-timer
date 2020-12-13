<template>
  <p>Reaction time: {{ score }} ms</p>
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
      this.rank = "Ninja reflexes 🥷🏽";
    } else if (this.score < 400) {
      this.rank = "Rapid reflexes 👌🏽";
    } else {
      this.rank = "Snail reflexes  👎🏽";
    }
  },
};
</script>

<style>
.rank {
  font-size: 1.3em;
  color: rgb(100, 84, 252);
  font-weight: 500;
}
</style>
