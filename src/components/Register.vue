<template>
  <form @submit.prevent="handleSubmit">
    <h3>Sign Up</h3>
    <div class="form-group">
      <label>First Name</label>
      <input type="text" class="form-control" v-model="firstName" placeholder="First Name"/>
    </div>
    <div class="form-group">
      <label>Last Name</label>
      <input type="text" class="form-control" v-model="lastName" placeholder="Last Name"/>
    </div>
    <div class="form-group">
      <label>Email</label>
      <input type="email" class="form-control" v-model="email" placeholder="Email"/>
    </div>
    <div class="form-group">
      <label>Password</label>
      <input type="password" class="form-control" v-model="password" placeholder="Password"/>
    </div>
    <div class="form-group">
      <label>Confirm Password</label>
      <input type="password" class="form-control" v-model="passwordConfirm" placeholder="Confirm Password"/>
    </div>
    <button class="btn btn-primary btn-block">Sign Up</button>
  </form>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Register',
  data () {
    return {
      firstName: '',
      lastName: '',
      email: '',
      password: '',
      passwordConfirm: ''
    }
  },
  methods: {
    async handleSubmit () {
      const data = {
        firstName: this.firstName,
        lastName: this.lastName,
        email: this.email,
        password: this.password,
        passwordConfirm: this.passwordConfirm
      }
      console.log(data)
      const response = await axios.post('user/register', data)

      console.log(response)
      this.$router.push('/login')
    }
  }
}
</script>

<style scoped>

</style>
