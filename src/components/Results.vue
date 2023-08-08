<template>
  <div>
    <p>Your Reaction Result: {{score}} ms</p>
    <p>{{rank}}</p>
  </div>
</template>

<script>
export default {
 props: ['score'],
 data () {
    return{
        rank: null,
    }
 },
 mounted() {
    if(this.score < 150){
        this.rank = 'CHEATER!!!!!!!!!'
    }else if(this.score < 250){
        this.rank = 'Fastest Finger'
    }else if(this.score < 400){
        this.rank = 'Nice speed'
    }else{
        this.rank = 'Snail pace....'
    }
 }
}
</script>

<style>
p{
    color: #26854e;
    font-weight: 600;
}
</style>