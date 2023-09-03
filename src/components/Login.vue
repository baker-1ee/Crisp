<template>
  <form @submit.prevent="handleSubmit">
    <error v-if="error" :error="error"/>
    <h3>Login</h3>
    <div class="mb-3">
      <label class="form-label">Email</label>
      <input v-model="email" class="form-control" placeholder="Email" type="email"/>
    </div>

    <div class="mb-3">
      <label class="form-label">Password</label>
      <input v-model="password" class="form-control" placeholder="Password" type="password"/>
    </div>

    <button class="btn btn-primary d-block w-100">Login</button>

    <p class="forgot-password text-right">
      <router-link to="forgot">Forgot password?</router-link>
    </p>

  </form>
</template>

<script>
import axios from 'axios'
import Error from './Error.vue'

export default {
  name: 'Login',
  components: {
    Error
  },
  data () {
    return {
      email: '',
      password: '',
      error: ''
    }
  },
  methods: {
    async handleSubmit () {
      try {
        const response = await axios.post('/api/v1/auth/authenticate',
          {
            email: this.email,
            password: this.password
          },
          {
            headers: {
              'Authorization': ''
            }
          })

        localStorage.setItem('token', response.data.token)
        await this.$store.dispatch('user', response.data.user)
        await this.$router.push('/')
      } catch (e) {
        this.error = 'Invalid username/password!'
      }
    }
  }
}
</script>

<style scoped>

</style>
