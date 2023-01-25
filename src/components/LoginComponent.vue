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

            let url = 'http://localhost:5050/users/login'

            let post = {
                username: this.username,
                password: this.password
            }

            axios.post(url, post)
                .then(responsed => {
                    if(responsed.data.user) {
                        window.location.href = 'http://localhost:8080/home';
                    }else {
                        this.alerta = 'No existe ese usuario magi'
                    }
                })
                .catch(error => console.log(error))

        }
    }
}
</script>

<template>
    <input type="text" v-model="username" placeholder="User">
    <input type="text" v-model="password" placeholder="Passwor">
    <button @click="login">Bien</button>
    <p>{{ alerta }}</p>
</template>
