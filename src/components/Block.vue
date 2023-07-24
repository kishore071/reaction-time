<template>
  <div class="block" @click="stopTimer" v-if="showBlocked">
    Click Me <br>
<!--     <p>Reaction Time: {{reactionrate}}ms</p>
    <button class="tjat" >remove</button> -->
  </div>
  <slot name="linked"></slot>
</template>

<script>
export default {
  props:['delay'],
  data(){
    return{
      showBlocked:false,
      timer:null,
      reactionrate:0,
  }},
  mounted(){
/*     console.log("mounted Succedded"); */
    setTimeout(()=>{
      this.showBlocked=true;
      this.startTimer();
    },this.delay)
  },
  unmounted(){
    console.log("unmounted Succedded");
  },
  updated(){
    console.log("updated Succedded "+this.showBlocked); 
  },
  methods:{
    emittion(){
          this.$emit('close');
          console.log('total time: '+this.delay);
    },
    startTimer(){
      this.timer=setInterval(()=>{
        this.reactionrate+=10
      },10)//this runs each 10ms(milliseconds)
    },
    stopTimer(){
      clearInterval(this.timer);//stops the setTimer for running
/*       console.log('total time: '+this.reactionrate); */
      this.$emit('result',this.reactionrate);
    },
  },
}
</script>

<style>
.block{
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}
 button{
  background-color: #0faf87;
  color:darkslateblue;
}
</style>