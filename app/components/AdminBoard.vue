<template>

<section class="main" >
  <h2>Messages</h2>
 <div>
        <button @click="loadMessages" >Load Messages</button>
      </div>
<ul>

<messages v-for="result in results" 
:key="result.id"  
:name="result.name"
:email="result.mail"
:subject="result.subject"
:message="result.message"
>
</messages>
</ul>
</section>
</template>

<script>
import Messages from './Messages';
import axios from "axios";


export default {
  components: {
    Messages,
       
      },

 data() {
    return {
      results: [],
         }
  },
 methods: {
   loadMessages() {
    axios.get('https://eglise-st-michel-default-rtdb.europe-west1.firebasedatabase.app//messages.json').then( (response) => {
    
       this.results = response.data;
    })
   .catch((error) => {
     console.log(error);
    //  on teste avec le .catch quand il n'y a pas de loading
    //  on mets le loading à false
  
   });
 },

},
 // quand ce composant user experiences sera exécuté, la fonction loadexperiences le sera  automatiquement
 
}
</script>

<style scoped>

</style>