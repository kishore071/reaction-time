<template>
  <p>
    <span v-if="showRes"> 
        <h2>Highest Reaction Score: {{list}} ms</h2>
        <h3>Current Reaction Score: {{scored}} ms</h3>
        <h4>
            <div class="rank">
                Remarks: {{ rank }}
            </div>
        </h4>
        <h1>Previous Reaction Scores:</h1>
        <li v-for="high in total" class="rank" :key="high">
            {{ high }} ms
        </li>
    </span>
    <span v-else>Either game is been started (or) No History of Game</span>
</p>
</template>

<script>
export default {
    props:['showRes','scored','list','total'],
    data(){
        return{
            rank:null,
        }
    },
    mounted(){
        if(this.scored<250){
            this.rank='Never Touched A Grass I see ';
        }
        else if(this.scored<400){
            this.rank='Not Bad I see U';
        }
        else{
            this.rank='Damn! Just Touched only Books Hah! ';
        }
    },
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
}
</style>