<template>
  <input type="text" v-model="username">

  <input type="text" v-model="password" placeholder="Password">  

  <button @click="save">Press me pls</button>
</template>

<script>

import axios from 'axios'
let url = 'http://localhost:5050/users/register'

export default {
name: "MyComponent",
data() {
  return {
    username: "",
    password: ""
  };
},

methods: {
  save: function(){
    let post = {
      username: this.username,
      password: this.password
    }
    try {
      axios.post(url, post)
        .then(response => console.log(response.data.msg))
        .then(data => window.location.href = 'http://localhost:5050/users/login')
      
      
    } catch (error) {
      console.log(error)
    }
  }
}

}


</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
