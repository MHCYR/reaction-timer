<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    click me!
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 200px;
  border-radius: 20px;
  background: rgb(63, 94, 251);
  background: radial-gradient(
    circle,
    #3f5efb 0%,
    #6447ce 70%,
    rgba(123, 57, 179, 1) 100%
  );
  color: white;
  text-align: center;
  padding: 100px;
  margin: 40px auto;
  font-size: 40px;
}
</style>
