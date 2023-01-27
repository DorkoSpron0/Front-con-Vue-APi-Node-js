<script>
import axios from 'axios';


export default {
    data() {
        return {
            username: '',
            password: '',
            alerta: '',
        };
    },
    methods: {
        login: function () {

            let url = 'http://localhost:8081/users/login'

            let post = {
                username: this.username,
                password: this.password
            }

            axios.post(url, post)
                .then(responsed => {
                    if (responsed.data.user) {
                        window.location.href = 'http://localhost:8080/home';
                    } else {
                        this.alerta = 'No existe ese usuario magi'
                    }
                })
                .catch(error => console.log(error))

        }
    }
}
</script>

<template>

    <div class="container bg-dark text-light mt-5 rounded shadow">
        <div class="row">
            <div class="col bg">

            </div>
            <div class="col">
                <div class="text-end">
                    <img src="../assets/logo.png" width="48" alt="" >
                </div>
                <h2 class="fw-bold text-center py-5">Login</h2>

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
                        <button @click="login" class="btn btn-primary">Submit</button>
                    </div>

                    <div class="my-3">
                        <span>U dont have account? <router-link to="/users/register">Register</router-link></span>
                    </div>
                </div>

            </div>
        </div>
    </div>

    <p>{{ alerta }}</p>
</template>

<style>
    .bg{
        background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/Gnulinux.svg/1200px-Gnulinux.svg.png');
        background-position: center center;
    }
    .bg{
        background-repeat: no-repeat;
        background-size: contain;
    }
</style>