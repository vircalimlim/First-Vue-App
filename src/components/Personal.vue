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
    <div id="home" class="container intro">
      <transition name="fade" appear>
        <div>
          <img src="@/assets/img/avatar.png" alt="image">
          <div class="para">
            <p>
              Hello I am Virgilio,
            </p>
            <p>
              an aspiring Web Developer
            </p>
          </div>
        </div>
      </transition>
    </div>

    <div id="about" class="container about-me">
      <h2>About Me</h2>
      <p>
        I'm Virgilio Calimlim, a college student in Philippine College of Science and Technology. My main focus is about Web Development. I enjoyed creating responsive and mobile friendly websites and systems using my knowledge of the following:
      </p>
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

    <div id="projects" class="container projects">
      <h2>Projects</h2>

      <div class="images">

        <div ref="imgParent" @click="zoom(image.id, $event)" :id="image.id" v-for="image in images" :key="image.id" class="img">
          <img :src="require('@/assets/img/'+image.pic)" alt="image" height="300" width="300">
        </div>


      </div>

    </div>

    <div v-show="overlay" @click.self="hide" class="container image-overlay">

      <svg @click="imageBack(count)" xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="currentColor" class="arrow bi bi-caret-left-fill" viewBox="0 0 16 16"> <path d="m3.86 8.753 5.482 4.796c.646.566 1.658.106 1.658-.753V3.204a1 1 0 0 0-1.659-.753l-5.48 4.796a1 1 0 0 0 0 1.506z" /> </svg>

      <div class="image-container">
        <div @click="hide" class="close">
          <span>&times;</span>

        </div>

        <img ref="img" src="" alt="image">

      </div>


      <svg @click="imageForward(count)" xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="currentColor" class="arrow bi bi-caret-right-fill" viewBox="0 0 16 16"> <path d="m12.14 8.753-5.482 4.796c-.646.566-1.658.106-1.658-.753V3.204a1 1 0 0 1 1.659-.753l5.48 4.796a1 1 0 0 1 0 1.506z" /> </svg>

    </div>

    <div id="contacts" class="container contacts">
      <div class="info">
        <h2>Contacts</h2>
        <p>
          <label>Email:</label> virgiliocalimlim@gmail.com
        </p>
        <p>
          <label>Github:</label> <a href="https://github.com/vircalimlim">virgiliocalimlim</a>
        </p>
        <p>
          <label>Mobile Number:</label> 09496127912
        </p>
      </div>
    </div>

  </div>
</template>

<script>
  export default {
    props: ['key'],
    data() {
      return {
        overlay: false,
        path: '../img/',
        images: [{
          'pic': 'login.jpg',
          'id': 1
        },
          {
            'pic': 'friend.jpg',
            'id': 2
          },
          {
            'pic': 'post.jpg',
            'id': 3
          },
          {
            'pic': 'profile.jpg',
            'id': 4
          }],
        count: 0,
      }
    },
    methods: {
      beforeEnter() {
        alert("before")
      },
      enter() {
        alert("enter")
      },
      afterEnter() {
        alert("after")
      },
      zoom(id, event) {
        if (event.target.src) {

          this.$refs.img.src = event.target.src
          this.overlay = true
          this.count = id-1

        } else {
          return false
        }
      },

      hide() {
        this.overlay = false
        clearInterval(this.destroyInterval)
      },

      pageScroll() {
        alert("scroll")
      },

      imageBack(id) {
        if (this.count <= 0) {
          this.count = parseInt(this.images.length-1)

          this.$refs.img.src = require('@/assets/img/'+ this.images[this.count]['pic'])

        } else {
          this.count--
          this.$refs.img.src = require('@/assets/img/'+ this.images[this.count]['pic'])
        }
      },

      imageForward(id) {
        if (this.count >= this.images.length-1) {
          this.count = 0
          this.$refs.img.src = require('@/assets/img/'+ this.images[this.count]['pic'])

        } else {
          this.count++
          this.$refs.img.src = require('@/assets/img/'+ this.images[this.count]['pic'])

        }

      }


    },


  }
  </script>

  <style scoped>

    .image-overlay {
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
    .image-container {
      padding: 10px 15px;
      position: relative;
    }
    .image-container .close {
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
      z-index: 999;

    }

    .image-overlay img {
      height: 60%;
      width: 250px;
      background: white;
      objdect-fit: contain;
      margdin: auto 0;
    }

    h2 {
      text-shadow: 0 0 2px rgba(0,0,0,.4);
      padding: 20px 10px;
    }

    .intro {
      width: 100%;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      background: #a3a3c2;
      min-height: 40vh;
      padding: 150px 15px 100px 15px;
    }
    .intro .para {
      height: 100%;
      margin: auto;
    }
    .intro img {
      height: 150px;
      width: 150px;
      padding: 0;
      margin: 0;
      border-radius: 180%;
      box-shadow: 0 3px 5px rgba(0,0,0, .4);
    }
    .intro div p:nth-child(1) {
      font-size: 40px;
      font-weight: bolder;
      color: #f0f0f5;
    }
    .intro div  p:nth-child(2) {
      font-size: 35px;
      font-weight: bolder;
      color: #1f1f2e;
    }

    .fade-enter-from {
      opacity: 0;
      transform: translateX(-90px);

    }
    .fade-enter-active {
      transition: all .6s ease;
    }


    ul {
      padding: 30px 15px 18px 15px;
    }
    ul li {
      font-weight: bold;
      margin: 0 0 10px 5px;
      background: #a3a3c2;
      border-radius: 20px;
      list-style-type: none;
      padding: 10px 20px;
      display: inline-block;
    }
    li:nth-child(3) {
      color: #ffffff;
      background: #f0db4f;
    }
    li:nth-child(1) {
      color: white;
      background: #f06529;
    }
    li:nth-child(2) {
      color: #ffffff;
      background: #2965f1;
    }
    li:nth-child(4) {
      color: #ffffff;
      background: #474A8A;
    }
    li:nth-child(5) {
      color: white;
      background: #00758f;
    }
    li:nth-child(6) {
      background-color: #563d76;
      color: #ffffff;
    }
    li:nth-child(7) {
      color: #ffffff;
      background: #0769ad;
    }
    li:nth-child(8) {
      color: #ffffff;
      background: #fb503b;
    }
    li:nth-child(9) {
      color: #ffffff;
      background: #42b883;
    }

    li:hover {
      transform: scale(.9);
      transition: all .4s ease;
    }
    .about-me {
      padding: 20px 15px;
      width: 100%;
    }
    .about-me p {
      font-style: italic;
      text-align: justify;
      font-size: 18px;
      margin-top: 5px;

    }

    img {
      background: black;
      object-fit: contain;
      webkit-object-fit: contain;
      padding: 10px 15px;
      margin-top: 10px;
      border: none;
      box-shadow: 0 0 5px rgba(0,0,0, .4);
    }
    .images {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-around;
    }


    .contacts {
      width: 100%;
      padding: 0px 15px;
      min-height: 200px;
      background: black;
      color: white;
      margin-top: 40px;
      text-align: left;
    }

    .info h2 {
      text-align: center;
    }
    .info p{
      margin-top: 10px;
    }

    a {
      text-decoration: none;
      color: white;
    }
    label {
      color: #7575a3;
      font-weight: bold;
    }

    .arrow {
      color: white;
    }


  </style>