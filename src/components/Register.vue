<template>
  <form @submit.prevent="handleSubmit">
    <error v-if="error" :error="error"/>
    <h3>Sign Up</h3>
    <div class="mb-3">
      <label class="form-label">Name</label>
      <input v-model="name" class="form-control" placeholder="Name" type="text"/>
    </div>
    <div class="mb-3">
      <label class="form-label">Email</label>
      <input v-model="email" class="form-control" placeholder="Email" type="email"/>
    </div>
    <div class="mb-3">
      <label class="form-label">Password</label>
      <input v-model="password" class="form-control" placeholder="Password" type="password"/>
    </div>
    <div class="mb-3">
      <label class="form-label">Confirm Password</label>
      <input v-model="passwordConfirm" class="form-control" placeholder="Confirm Password" type="password"/>
    </div>
    <button class="btn btn-primary d-block w-100">Sign Up</button>
  </form>
</template>

<script>
import axios from 'axios'
import Error from './Error.vue'

export default {
  name: 'Register',
  components: {Error},
  data () {
    return {
      name: '',
      email: '',
      password: '',
      passwordConfirm: '',
      error: ''
    }
  },
  methods: {
    async handleSubmit () {
      try {
        const data = {
          name: this.name,
          email: this.email,
          password: this.password
        }
        await axios.post('/api/v1/auth/register', data, {
          headers: {
            'Authorization': ''
          }
        })
        await this.$router.push('/login')
      } catch (e) {
        this.error = 'Error occurred!'
      }
    }
  }
}
</script>

<style scoped>

</style>
