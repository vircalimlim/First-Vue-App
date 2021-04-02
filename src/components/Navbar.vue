<template>
  <div class="bg">

    <div class="title">
      <span>Portfolio</span>
    </div>

    <div class="content">
      <button @click="toggle">
        <svg xmlns="http://www.w3.org/2000/svg" width="45" height="45" fill="currentColor" class="bi bi-list" viewBox="0 0 16 16"> <path fill-rule="evenodd" d="M2.5 11.5A.5.5 0 0 1 3 11h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4A.5.5 0 0 1 3 7h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4A.5.5 0 0 1 3 3h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z" /> </svg>
      </button>
    </div>

    <transition name="toggle">
      <div v-if="show" class="dropdown">
        <ul>
          <li><a href="#home">Home</a></li>
          <li><a href="#about">About</a></li>
          <li><a href="#projects">Projects</a></li>
          <li><a href="#contacts">Contacts</a></li>
        </ul>
      </div>
    </transition>

  </div>
</template>


<script>
  export default {
    data() {
      return {
        show: false,
      }
    },
    methods: {
      toggle() {
        this.show = !this.show
      }
    }
  }
  </script>


  <style scoped>

    .bg {
      z-index: 9;
      display: block;
      background: black;
      padding: 4px 10px;
      min-height: 3rem;
      width: 100%;
      position: fixed;
    }
    .content {
      position: absolute;
      right: 3px;
      top: 4px;
      text-align: right;
    }
    button {
      font-size: 20px;
      font-weight: bolder;
      height: 3rem;
      margin: 0;
      padding: 0 10px;
      color: #52527a;
      border: none;
      outline: none;
      background-color: black;
    }
    button:hover {
      color: white;
    }

    .title {
      font-weight: bolder;
      text-align: left;
      font-size: 2rem;
      color: white;
      padding: 5px;
    }

    .dropdown {
      text-align: left;
      color: white;
      padding: 5px 20px;
    }
    a {
      text-decoration: none;
      color: white;
      font-weight: bold;
      display: block;
    }
    li {
      list-style-type: none;
      padding: 10px 0;
    }
    li:hover {
      background-color: #666699;
      padding: 10px 10px;
    }

    .toggle-enter-from, .toggle-leave-to {
      opacity: 0;
      transform: translateX(-50px);

    }

    .toggle-enter-active, .toggle-leave-active {
      transition: all .3s ease;
    }
  </style>