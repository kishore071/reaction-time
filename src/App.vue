<template>
  <h1>Reaction Timer</h1>
  <button @click="Start" :disabled="isPlaying">Play</button>
  <Block @close="Start" v-if="isPlaying" :delay="delay" @result="EndGame"/>
  <Results :showRes="showRes" :scored="Score" :list="maxim" :total="userscore"/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue';
export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  props:{},
  data() {
    return {
      isPlaying: false,
      delay:null,
      Score:null,
      showRes:false,
      userscore:[],
      maxim:0,
    }
  },
  methods: {
    Start(){
      this.delay=2000+Math.random()*5000;//mostly lt could be 7000ms least could be 2000ms
      this.isPlaying = !this.isPlaying;
      this.showRes=false;
      console.log(this.delay);
    },
    EndGame(FinalTime){
      this.Score=FinalTime;
      this.isPlaying=false;
      this.showRes=true;
      this.userscore.push(FinalTime);
      /* console.log(this.userscore); */
      this.maxim=Math.min(...this.userscore)
      /* console.log("MAxim: ",this.maxim);
      console.log("Scores: ",this.Score); */
    },
  },
  computed:{
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button{
  size: 90cm;
  align-items: center;
  color: blueviolet;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
