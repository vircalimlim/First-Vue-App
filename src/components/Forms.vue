<template>
  <form @submit.prevent="handleSubmit">
  <div class="form-group">
    <label>Name</label>
    <input type="text" v-model="name">
  </div>
  
  <div class="form-group">
    <label>Email</label>
    <input type="text" v-model="email">
    <p>{{emailError}}</p>
  </div>
  
  <div class="form-group">
    <label>
    <input type="checkbox" v-model="terms">Terms and Policies</label>
  </div>
  
  <div class="form-group">
    <label>
    <input type="checkbox" v-model="persons" value="Vir">Vir</label>
  </div>
  
  <div class="form-group">
    <label>
    <input type="checkbox" v-model="persons" value="Padilla">Padilla</label>
  </div>
  
  <div class="form-group">
    <label>
    <input type="checkbox" v-model="persons" value="Calimlim">Calimlim</label>
  </div>
  
  <div class="form-group">
    <p>Name: {{name}}</p>
    <p>Email: {{email}}</p>
    <p>Checkbox Status: {{terms}}</p>
    <p>Selected Persons: {{persons}}</p>
  </div>
  
  <div class="form-group btn">
    <button>Submit</button>
  </div>
</form>
</template>

<script>
  export default{
    data(){
      return{
        name: '',
        email: '',
        terms: false, 
        persons: [],
        emailError: ''
      }
    },
    
    methods: {
      handleSubmit(){
        this.emailError = this.email.length < 5 ? 'Email too short' : ''
      }
    }
  }
</script>


<style>
html{
  background-color: #f3f3f3;
}
  *{
    margin: 0;
    padding: 0;
  }
  form{
    padding: 20px;
    background-color: white;
  }
  .form-group{
    bordser-bottom: 2px solid gray;
    margin-top: 20px;
  }
  input[type="text"]{
    border: 0;
    border-bottom: 4px solid #f3f3f3;
    outline: none ;
    outline-color: gray;
    font-size: 19px;
    padding: 2px 3px;
    width: 80vw;
    
  }
  input[type="checkbox"]{
    color: blue;
    background: blue;
    height: 20px;
    width: 20px;
    margin: 0 4px;
  }
  label{
    display: block;
    font-weight: bold;
    color: gray;
  }
  button{
    border: 0;
    border-radius: 20px;
    padding: 10px 30px;
    background-color: blue;
    color: white;
    font-weight: bolder;
    outline: none;
    cursor: pointer;
  }
  .btn{
    text-align: center;
  }
  
</style>