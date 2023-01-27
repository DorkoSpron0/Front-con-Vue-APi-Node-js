<template>

<div class="container bg-dark text-light mt-5 rounded shadow">
        <div class="row">
            <div class="col bg">

            </div>
            <div class="col">
                <div class="text-end">
                    <img src="../assets/logo.png" width="48" alt="" >
                </div>
                <h2 class="fw-bold text-center py-5">Register</h2>

                <!-- LOGIN -->
                
                <div class="form">
                    <div class="mb-4">
                        <label for="email" class="form-label">Email</label>
                        <input type="email" class="form-control" v-model="username" placeholder="Username"/>
                    </div>

                    <div class="mb-4">
                        <label for="password" class="form-label">Password</label>
                        <input type="password" class="form-control" v-model="password" placeholder="Password"/>
                    </div>

                    <div class="d-grid">
                        <button @click="save" class="btn btn-primary">Submit</button>
                    </div>

                    <div class="my-3">
                        <span>U have already an account? Login <router-link to="/users/login">Here</router-link></span>
                    </div>
                </div>

            </div>
        </div>
    </div>
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
        .then(data => window.location.href = 'http://localhost:8081/users/login')
      
      
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
