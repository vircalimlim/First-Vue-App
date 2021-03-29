<template>
  <div class="component-container">
    
   <!-- <div class="personal">
      <h2>Personal Information</h2>
      <ul>
        
      <li>
      <p>Name: Virgilio Jr. P. Calimlim</p>
      </li>
      
      <li>
        <p>Address: C. Bogtong Malasiqui, Pangasinan</p>
      </li>
      
      <li>
      <p>Age: 21</p>
      </li>
      
      </ul>
    </div>-->
    <div id="home" class="intro">
    <transition name="fade" appear>
      <div>
        <img src="@/assets/vir.github.io/img/avatar.png" alt="image">
        <div class="para">
      <p>Hello I am Virgilio,</p>
      <p>an aspiring Web Developer</p>
        </div>
      </div>
    </transition>
    </div>
    
    <div id="about" class="about-me">
      <h2>About Me</h2>
      <p>I'm Virgilio Calimlim, a college student in Philippine College of Science and Technology. My main focus is about Web Development. I enjoyed creating responsive and mobile friendly websites and systems using my knowledge of the following:</p>
      <ul>
        <li>HTML</li>
        <li>CSS</li>
        <li>JAVASCRIPT</li>
        <li>PHP</li>
        <li>SQL DATABASE</li>
        <li>BOOTSTRAP</li>
        <li>JQUERY</li>
        <li>LARAVEL</li>
        <li>VUE</li>
      </ul>
    </div>
    
    <div id="projects" class="projects">
      <h2>Projects</h2>
      
    <div class="images">
      
      <div ref="imgParent" @click="zoom(image.id, $event)" :id="image.id" v-for="image in images" :key="image.id" class="img">
        <img :src="require('@/assets/vir.github.io/img/'+image.pic)" alt="image" height="300" width="300">
      </div>

      
      </div>
      
    </div>
    
    <div v-show="overlay" @click.self="hide" class="image-overlay">
      
      <div class="image-container">
      <div @click="hide" class="close">
      <span>&times;</span>
      </div>

      <img ref="img" src="" alt="image">
      </div>
      
    </div>
    
    <div id="contacts" class="contacts">
      <div class="info">
      <h2>Contacts</h2>
      <p><label>Email:</label> virgiliocalimlim@gmail.com </p>
      <p><label>Github:</label> <a href="https://github.com/killerfinisher12">virgiliocalimlim</a></p>
      <p><label>Mobile Number:</label> 09496127912</p>
      </div>
    </div>
    
  </div>
</template>

<script>
  export default{
    props: ['key'],
    data(){
      return{
        overlay: false,
        path: '../img/',
        images: [
          {'pic' : 'login.jpg', 'id': 1},
          {'pic' : 'friend.jpg', 'id': 2},
          {'pic' : 'post.jpg', 'id': 3},
          {'pic' : 'profile.jpg', 'id': 4}
          ],
        count: 0,
        obj: null,
        destroyInterval: null
      }
    },
    methods: {
      zoom(id, event){
        if(event.target.src){
          
          this.$refs.img.src = event.target.src
          this.overlay = true
          this.imageChange(id)
        }
        else{
          return false
        }
      },
      
    hide(){
      this.overlay = false
      clearInterval(this.destroyInterval)
    },
    
    pageScroll(){
      alert("scroll")
    },
    
    imageChange(id){
      this.count = id
      this.destroyInterval = setInterval(() =>{
        if(this.count > this.images.length-1){
          this.count = 0
          
        }
        else{
        this.$refs.img.src = require('@/assets/vir.github.io/img/'+ this.images[this.count++]['pic'])
        }

      }, 2500)

    }
    
    
    },
destoyed: function(){ 
  clearInterval( this.imageChange )
  },
    
  }
</script>

<style scoped>

    .image-overlay{
      display: flex;
      justify-content: center;
      align-items: center;
      background-color: rgba(0,0,0, .8);
      position: fixed;
      top: 0;
      height: 100%;
      width: 100%;
      z-index: 99;
      margin: 0;
      padding: 0;
    }
    .image-container{
      padding: 10px 15px;
      position: relative;
    }
    .image-container .close{
      position: absolute;
      top: 10px;
      right: 6px;
      margin: 0;
      font-size: 26px;
      color: white;
      font-weight: bold;
      background-color: gray;
      border-radius: 20px;
      height: 30px;
      width: 30px;
      
    }
    
    .image-overlay img{
      height: 60%;
      width: 250px;
      background: white;
      objdect-fit: contain;
      margdin: auto 0;
    }

    h2{
      color: rxed;
    text-shadow: 0 0 2px rgba(0,0,0,.4);
  }
  
  .intro{
    width: 100%;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    background: #a3a3c2;
    min-height: 40vh;
    padding: 150px 10px 100px 10px;
  }
  .intro .para{
    height: 100%;
    margin: auto;
  }
  .intro img{
    height: 150px;
    width: 150px;
    padding: 0;
    margin: 0;
    border-radius: 180%;
    box-shadow: 0 3px 5px rgba(0,0,0, .4);
  }
 .intro div p:nth-child(1){
    font-size: 40px;
    font-weight: bolder;
    color: #f0f0f5;
  }
.intro div  p:nth-child(2){
    font-size: 35px;
    font-weight: bolder;
    color: #1f1f2e;
  }
  
  .fade-enter-from{
    opacity: 0;
    transform: translateX(-90px);
    
  }
  .fade-enter-active{
    transition: all .6s ease;
  }
  

  ul{
    padding: 30px 0 18px 0;
  }
  ul li{
    font-weight: bold;
    margin:0 0 10px 5px;
    background: #a3a3c2;
    border-radius: 20px;
    list-style-type: none;
    padding: 10px 20px;
    display: inline-block;
  }
  li:nth-child(3){
    colzor: crimson;
    background: #f0db4f;
  }
  li:nth-child(1){
    color: white;
    background: #f06529;
  }
  li:nth-child(2){
    color: #ffffff;
    background: #2965f1;
  }
  li:nth-child(4){
    color: #b0b3d6;
    background: #474A8A;
  }
  li:nth-child(5){
    color: #f29111;
    background: #00758f;
  }
  
  
  li:hover{
    madrgin-left: 5px;
    transform: scale(.9);
    transition: all .4s ease;
    backgxround: #f0f0f5;
  }
  .about-me{
    padding: 20px 10px;
    width: 100%;
  }
  .about-me p{
    font-style: italic;
    text-align: justify;
    font-size: 18px;
    margin-top: 5px;
    
  }
  
  img{
    background: black;
    object-fit: contain;
    webkit-object-fit: contain;
    padding: 10px 0;
    margin-top: 10px;
    border: none;
    box-shadow: 0 0 5px rgba(0,0,0, .4);
  }
  .images{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
  }
  
  
  .contacts{
    width: 100%;
    padding: 10px;
    min-height: 200px;
    background: black;
    color: white;
    margin-top: 40px;
  }
  .info{
    padding: 40px 0 0 0;
  }
  .info h2{
    margin-bottom: 10px;
  }
  
  a{
    text-decoration: none;
    color: white;
  }
  label{
    color: #7575a3;
    font-weight: bold;
  }
    
</style>