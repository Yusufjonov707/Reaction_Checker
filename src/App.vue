<template>
  <div>
    <h1>Reaction Chacker</h1>
    <button class="button" @click="start" :disabled="Isplaying">Start</button>
    <Block v-if="Isplaying" :delay="delay" @end="endGame"/>
    <Results v-if="showresult" :score ="score" />
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
      
export default {
  name: 'App',
  components: { Block, Results },
  data () {
    return {
      Isplaying : false,
      delay : null,
      score : null,
      showresult: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000,
      this.Isplaying = true,
      this.showresult = false
    },
    endGame(reactionTime) {
      this.score = reactionTime,
      this.Isplaying = false,
      this.showresult = true
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
  color: #2c3e50;
  margin-top: 60px;
}
.button {
  background-color: #c2fbd7;
  border-radius: 100px;
  box-shadow: rgba(44, 187, 99, .2) 0 -25px 18px -14px inset,rgba(44, 187, 99, .15) 0 1px 2px,rgba(44, 187, 99, .15) 0 2px 4px,rgba(44, 187, 99, .15) 0 4px 8px,rgba(44, 187, 99, .15) 0 8px 16px,rgba(44, 187, 99, .15) 0 16px 32px;
  color: green;
  cursor: pointer;
  display: inline-block;
  font-family: CerebriSans-Regular,-apple-system,system-ui,Roboto,sans-serif;
  padding: 7px 20px;
  text-align: center;
  text-decoration: none;
  transition: all 250ms;
  border: 0;
  font-size: 16px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
}
.button-33:hover {
  box-shadow: rgba(44,187,99,.35) 0 -25px 18px -14px inset,rgba(44,187,99,.25) 0 1px 2px,rgba(44,187,99,.25) 0 2px 4px,rgba(44,187,99,.25) 0 4px 8px,rgba(44,187,99,.25) 0 8px 16px,rgba(44,187,99,.25) 0 16px 32px;
  transform: scale(1.05) rotate(-1deg);
}
.button[disabled]{
  opacity:0.2;
  cursor:not-allowed;
}
</style>
