<template>
  <div class="parent" @click.self="closeModal">
    <div class="parent-content">
      
      <slot></slot>

      <h1>{{ header }}</h1>
      <h1 class="default" :class="{prop: prop == true}">{{footer}}</h1>
      
      <slot name="links"></slot>
      
    </div>
  </div>
</template>

<script>
  export default{
    data(){
      return{
        prop: true
      }
    },
    methods: {
      closeModal(){
        this.$emit('close')
      }
    },
    props: ['header', 'footer']
  }
</script>

<style>
  *{
    margin: 0;
  }
  .parent{
    position: fixed;
    top: 0;
    bottom: 0;
    height: 100%;
    width: 100%;
    background-color: gray;
    color: green;
    font-weight: bolder;
    padding: 20px;
    text-align: center;
  }
  .parent-content{
    position: fixed;
    top: 90px;
    left: 30px;
    min-height: 200px;
    width: 80vw;
    background-color: white;
  }
  .prop{
    color: white;
    text-shadow: 0 0 10px rgba(0,0,0, .5);
  }
  .default{
    border-bottom: 2px solid black;
  }
</style>