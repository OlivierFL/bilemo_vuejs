<template>
  <form
    id="login"
    method="post"
    class="w-full"
    @submit.prevent="handleSubmit"
  >
    <div class="w-full mb-5">
      <label
        for="username"
        class="font-jura font-bold text-left text-xl mb-2 block"
      >Nom <span
        class="text-red-500"
      >*</span></label>
      <input
        id="username"
        v-model.trim="username"
        type="text"
        name="username"
        required
        class="pt-3 pb-2 pl-2 block w-full px-0 mt-0 border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 border-gray-200 focus:shadow-md"
      >
    </div>

    <div class="w-full mb-10">
      <label
        for="password"
        class="font-jura font-bold text-left text-xl mb-2 block"
      >Mot de passe <span
        class="text-red-500"
      >*</span></label>
      <input
        id="password"
        v-model.trim="password"
        type="password"
        name="password"
        required
        class="pt-3 pb-2 pl-2 block w-full px-0 mt-0 border-0 border-b-2 appearance-none focus:outline-none focus:ring-0 focus:border-blue-600 border-gray-200 focus:shadow-md"
      >
    </div>

    <button
      id="button"
      form="login"
      type="submit"
      class="bg-blue-600 hover:bg-blue-700 text-white py-3 px-5 rounded-md hover:shadow-md w-1/2 focus:outline-none focus:ring focus:ring-blue-600 transition ease-in-out"
      :class="{ 'cursor-not-allowed opacity-30': isDisabled }"
      :disabled="isDisabled"
    >
      Connexion
    </button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  name: 'LoginForm',
  data () {
    return {
      username: null,
      password: null,
      isLoading: false,
      error: null
    }
  },
  computed: {
    isDisabled () {
      return !this.username || !this.password
    }
  },
  methods: {
    async handleSubmit () {
      this.isLoading = this.toggleLoader()
      let response = null
      try {
        response = await axios.post('http://localhost:8000/api/login_check', {
            'username': this.username,
            'password': this.password,
          },
          {
            headers: {
              'Access-Control-Allow-Origin': '*'
            }
          }
        )
      } catch (e) {
        this.isLoading = this.toggleLoader()
        this.error = e
      }
      console.log(response)
    },
    toggleLoader () {
      return !this.isLoading
    }
  }
}
</script>

<style scoped>
</style>
