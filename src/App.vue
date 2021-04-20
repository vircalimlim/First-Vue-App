<template>
  <Navbar></Navbar>
  <div class="containder">
  <Personal></Personal>
</div>
</template>

<script>
import Navbar from '@/components/Navbar.vue'
  import Personal from '@/components/Personal.vue'
  export default{
  
  components: {
    Navbar,
    Personal,
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
}
*{
  scroll-behavior: smooth;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  word-break: break-word;
  font-family:"Proxima Nova Soft W03 Regular";
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -webkit-text-stroke-width: 0.2px;
  -moz-osx-font-smoothing: grayscale;
  
}
@font-face{
    font-family: "Proxima Nova Soft W03 Regular"; 
    src: url("assets/font/f1448054f14757d284c064b271c00cc6.eot"); /* IE9*/ 
    
    src: url("assets/font/f1448054f14757d284c064b271c00cc6.eot?#iefix") format("embedded-opentype"), /* IE6-IE8 */ 
    
    url("assets/font/f1448054f14757d284c064b271c00cc6.woff2") format("woff2"), /* chrome、firefox */ 
    
    url("assets/font/f1448054f14757d284c064b271c00cc6.woff") format("woff"), /* chrome、firefox */ 
    
    url("assets/font/f1448054f14757d284c064b271c00cc6.ttf") format("truetype"), /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/ 
    
    url("assets/font/f1448054f14757d284c064b271c00cc6.svg#Proxima Nova Soft W03 Regular") format("svg"); /* iOS 4.1- */ 
}

@media (min-width:320px)  { 
  /* smartphones, iPhone, portrait 480x320 phones */ 
  }
@media (min-width:481px)  { 
  /* portrait e-readers (Nook/Kindle), smaller tablets @ 600 or @ 640 wide. */ 
  }
@media (min-width:641px)  { 
  /* portrait tablets, portrait iPad, landscape e-readers, landscape 800x480 or 854x480 phones */ 
  }
@media (min-width:961px)  { 
  /* tablet, landscape iPad, lo-res laptops ands desktops */ 
  .container{
  padding: 0 50px;
}
  }
@media (min-width:1025px) { 
  .container{
  padding: 0 150px;
}
  }
@media (min-width:1281px) { 
  /* hi-res laptops and desktops */ 
  }


</style>
