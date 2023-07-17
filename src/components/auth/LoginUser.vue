<template>
  <div class="vue-tempalte">
    <div class="App">
      <div class="vertical-center">
        <div class="inner-block">
          <div class="justify-content-evenly">
            <div class="vue-tempalte">
              <div v-if="!registerActive" class="card login p-3" v-bind:class="{ error: emptyFields }">
                <form>
                  <h3>Sign In</h3>
                  <div class="form-group mb-3">
                    <label>Email address</label>
                    <input v-model="emailLogin" type="email" class="form-control form-control-lg" required/>
                  </div>
                  <div class="form-group mb-3">
                    <label>Password</label>
                    <input v-model="passwordLogin" type="password" class="form-control form-control-lg" required/>
                  </div>
                  <div class="text-center">
                    <button type="button" @click="doLogin" class="btn btn-dark btn-lg btn-block">Sign In</button>
                  </div>
                  <p class="forgot-password text-right mt-2 mb-4">
                    Don't have an account? <a href="#" @click="registerActive = !registerActive, emptyFields = false">Sign
                    Up</a>
                    <br>
                    <br>
                    <router-link to="/forgot-password">Forgot password ?</router-link>
                  </p>
                </form>
              </div>

              <div v-else class="card register p-3" v-bind:class="{ error: emptyFields }">
                <form>
                  <h3>Sign Up</h3>
                  <div class="form-group mb-3">
                    <label>Full Name</label>
                    <input v-model="nameRegister" type="text" class="form-control form-control-lg" required/>
                  </div>
                  <div class="form-group mb-3">
                    <label>Email address</label>
                    <input v-model="emailRegister" type="email" class="form-control form-control-lg" required/>
                  </div>
                  <div class="form-group mb-3">
                    <label>Password</label>
                    <input v-model="passwordRegister" type="password" class="form-control form-control-lg" required/>
                  </div>
                  <div class="text-center">
                    <button type="button" @click="doRegister" class="btn btn-dark btn-lg btn-block">Sign Up</button>
                  </div>
                  <p class="forgot-password text-right mb-3">
                    Already registered? <a href="#" @click="registerActive = !registerActive, emptyFields = false">Sign
                    In</a>
                  </p>
                </form>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import '@/assets/css/main.css'

const axios = require('axios')
export default {
  name: 'LoginUser',
  data: function () {
    return {
      registerActive: false,
      emailLogin: '',
      passwordLogin: '',
      nameRegister: '',
      emailRegister: '',
      passwordRegister: '',
      emptyFields: false,
      baseUrl: 'http://localhost:8000/api'
    }
  },
  methods: {
    doLogin() {
      if (this.emailLogin === '' || this.passwordLogin === '') {
        this.emptyFields = true
      } else {
        // eslint-disable-next-line no-inner-declarations
        async function login(email, password) {
          const response = await axios.post(this.baseUrl + '/login', {
            email: email,
            password: password
          })
          console.log(response)
          if (response.status === 200) {
            await this.$router.push({ path: '/home' })
          }
        }

        login(this.emailLogin, this.passwordLogin)
      }
    },
    async doRegister() {
      if (this.nameRegister === "" || this.emailRegister === "" || this.passwordRegister === "") {
        this.emptyFields = true
      } else {
        console.log('call register')
        await axios.post(this.baseUrl + '/register', {
          name: this.nameRegister,
          email: this.emailRegister,
          password: this.passwordRegister
        }).then(result => {
          console.log(result);
          this.$router.push({name: 'home'})
          return result;
        }).catch(error => {
          console.log(error);
          throw error;
        });
      }
    }
  }
}
</script>