<template>
  <br>
  <span>Result: {{ result }}ms</span>
  <p>{{rank}}</p>
</template>

<script>
  export default{
    props: ['result'],
    data(){
      return {
        rank: null
      }
    },
    mounted(){
      if(this.result <=200){
        this.rank = "Yamete"
      }
      else if(this.result <= 400){
        this.rank = "Faster"
      }
      else{
        this.rank = "Slowly but surely"
      }
    }
  }
</script>

<style>
  
</style>