<template>
 <div class="background"  >
  <div class="style-form" >
    <form  v-on:submit.prevent="checkForm" class="form" >
    
    <div class="form-control" :class="{invalid: userNameValidity ==='invalid'}" >
      <label for="Votre nom">Votre Nom</label>
    <input type="text" id="user-name" name="user-name" v-model.trim="userName"/>
    </div>
    <p class="errormessage" v-if="userNameValidity ==='invalid'" >Merci de saisir votre nom</p>

    <div class="form-control" :class="{invalid: emailValidity ==='invalid'}" >
      <label for="Votre adresse Mail">Votre email</label>
     <input type="text" id="email" name="email" v-model.trim="email"/>
    </div>
    <p class="errormessage" v-if="emailValidity ==='invalid'" >Merci de saisir votre email</p>
  
   <div class="form-control" :class="{invalid: sujetValidity ==='invalid'}" >
  <label for="Sujet">Sujet</label>
    <input type="text" id="sujet" name="sujet" v-model.trim="sujet">
    </div>
 <p class="errormessage" v-if="sujetValidity ==='invalid'" >Merci de saisir le champs sujet</p>

    <div class="form-control" :class="{invalid: textValidity ==='invalid'}" >
    <textarea name="sujet" id="" cols="30" rows="10" v-model.trim="text" >
    </textarea>
    </div>
    <p class="errormessage" v-if="textValidity ==='invalid'" >Merci de saisir votre demande</p>
 
    <div>
    <button> Envoyer</button>
    </div>

  </form>
  </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      userName:'',
      email: '',
      sujet:"",
      text:"",
      errorList: [],
      userNameValidity:'pending',
      emailValidity:'pending',
      sujetValidity:'pending',
      textValidity:'pending',
    }
  },
  methods: {
    checkForm() {
        if (this.userName === '') {
         this.userNameValidity='invalid';
       } else{
         this.userNameValidity='valid';
       }
        if (this.email === '') {
         this.emailValidity='invalid';
       } else{
         this.emailValidity='valid';
       }
        if (this.sujet === '') {
         this.sujetValidity='invalid';
       } else{
         this.sujetValidity='valid';
       }
         if (this.text === '') {
         this.textValidity='invalid';
       } else{
         this.textValidity='valid';
       }
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