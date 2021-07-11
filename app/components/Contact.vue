<template>
 <div class="background"  >
  <div class="style-form" >
    <form  v-on:submit.prevent="checkForm" class="form" >
    
    <div class="form-control">
      <label for="Votre nom">Votre Nom</label>
    <input type="text" id="user-name" name="user-name" v-model.trim="userName"/>
    </div>
    
    <div class="form-control">
      <label for="Votre adresse Mail">Votre email</label>
     <input type="text" id="email" name="email" v-model.trim="email"/>
    </div>
   
  
   <div class="form-control" >
  <label for="Sujet">Sujet</label>
    <input type="text" id="sujet" name="sujet" v-model.trim="sujet">
    </div>
 
    <div class="form-control">
    <textarea name="sujet" id="" cols="30" rows="10" v-model.trim="text" >
    </textarea>
    </div>
        <div>
    <button> Envoyer</button>
    </div>
 <p v-if="invalidInput"> One or more input fields are invalid. Please check your provided data.</p>
        <p v-if="error">{{error}}</p>
  </form>
  </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      userName:'',
      email: '',
      sujet:'',
      text:'',
      invalidInput: false,
      error:null,
      
    }
  },
  methods: {
    checkForm() {
        if (this.userName === '' || this.email === '' || this.sujet === '' || this.text === '') {
        this.invalidInput = true;
        return;
      }
      this.invalidInput = false;
      this.error= null;
     
      
       axios.post('https://eglise-st-michel-default-rtdb.europe-west1.firebasedatabase.app//messages.json', {
       name: this.userName,
       mail: this.email,
       subject: this.sujet,
       message: this.text,
       
        })
        // permets d'idnquer une erreur côté serveur 
        .catch((error) => {
        console.log(error);
        this.error ='failed to execute the request . Try it later'
        }),
      this.userName = '',
      this.email='',
      this.sujet='',
      this.text=''
}
}
}
</script>

<style scoped>
@import '../assets/scss/_formulaire';

.form-control.invalid input{
  border-color: grey;
}
.errormessage{
  color: grey;
  font-weight: 700;
}
.background {
  background:lightgrey;
  background:contain;
  height: 100vh;
  width: 100vw;
  padding-top:20px
}
input {
  display:flex;
  margin-bottom:25px;
  border-radius:10px;
  width: 15vw;
  height: 2vw;
}
textarea{
  margin-top:15px;
  border-radius:10px;
  width:15vw;
  height: 25vh;
}
.style-form{
  display:flex;
  margin:0;
  padding:180px;
  margin: auto;
  max-width: 40rem
}
.textarea:not([rows]) {
    max-height: 60em;
    min-height: 30em;
   
}
button {
  margin-top: 10px;
  width:15vw;
  border-radius:10px;
  height: 5vh;
  font-size:x-large
  
}

</style>