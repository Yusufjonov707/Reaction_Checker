<template>
  <div class="block" v-if="showblock" @click="stopTimer">
    Click here
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
      return {
        showblock : false,
        time : null,
        reactionTime: 0
      }
    },
    mounted() {
      setTimeout(() => {
        this.showblock = true,
        this.startTimer()
      }, this.delay);
    },
    methods: {
      startTimer() {
        this.time = setInterval( ()=> {
          this.reactionTime += 10
        },10)
      },
    stopTimer() {
      clearInterval(this.time),
      this.$emit('end',this.reactionTime)
    }
  },
}
</script>

<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #26854e;
    color:white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
</style>