<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <div class="content">
      Click Me
    </div>
  </div>
</template>

<script>
  export default{
    props: ['delay'],
    data(){
    return {
      showBlock: false,
      time: null,
      reactiontimer: 0
    }
    },
    mounted() {
        setTimeout(() => {
          this.showBlock = true
          this.startTimer()
        }, this.delay)
    },
    methods: {
      startTimer(){
      this.timer =  setInterval(()=> {
          this.reactiontimer += 10
        }, 10)
      },
      stopTimer(){
        clearInterval(this.timer)
        //alert(this.reactiontimer)
        this.$emit('end', this.reactiontimer)
      }
    }
  }
</script>

<style>
 .block{
   height: 200px;
   width: 90%;
   padding: 40px 0;
   margin: 40px auto;
   background-color: green;
 } 
 .content{
   color: white;
   font-weight: bold;
   margin: 60px auto;
 }
</style>