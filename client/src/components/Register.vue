<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
        <br>      
        <div class="pl-4 pr-4 pt-2 pb-2"> 
          <v-text-field
            label="Email"
            v-model="email"
          ></v-text-field>
          <br>
          <v-text-field
            label="Password"
            type="password"
            v-model="password"
            autocomplete="new-password" />
          </v-text-field>
          <br>
          <div class="error" v-html="error" />
          <br>
          <v-btn dark class="cyan" @click="register">
            Register
          </v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthentificationService'
export default {
  
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register(){
      try {
        await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>
<style scoped>
.error {
  color: red;
}
</style>

