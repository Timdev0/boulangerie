<template>
    <div id="navbar-component">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link> |
        <router-link to="/doc">Doc</router-link> |
        <router-link to ="/sondage">Sondage</router-link>
    </div>
</template>

<style scoped>
    #navbar-component {
    padding: 30px;
    text-align: center;
    }

    #navbar-component a {
    font-weight: bold;
    color: #2c3e50;
    }

    #navbar-component a.router-link-exact-active {
    color: #42b983;
    }
</style>
