<script>
    import HomeView from './views/HomeView.vue';

    export default {
        data() {
            return {}
        },
        components: {
            HomeView
        }
    }
</script>

<template>
    <nav>
        <router-link to="/users/register">Register</router-link> |
        <router-link to="/users/login">Login</router-link>
    </nav>
    <router-view/>
</template>

<style>
</style>
