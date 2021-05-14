<template>
  <Nav />
  <div class="container w-10/12 md:w-2/3 max-w-2xl mx-auto mt-16 bg-gray-100 rounded-2xl shadow-md p-10 md:p-20 flex flex-col items-center">
    <h1 class="text-4xl font-jura font-bold mb-10">
      Connexion
    </h1>
    <LoginForm />
  </div>
</template>

<script setup>
import HelloWorld from './components/HelloWorld.vue'
import Nav from './components/Nav.vue'
import LoginForm from './components/Form/LoginForm.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
