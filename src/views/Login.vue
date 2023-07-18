<style>
body {
  font-family: Arial, Helvetica, sans-serif;
  background-color: #38a169;
}

/* Full-width input fields */
input[type=text], input[type=password] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

/* Set a style for all buttons */
button {
  background-color: #04aa6d;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  cursor: pointer;
  width: 100%;
}

button:hover {
  opacity: 0.8;
}

/* Center the image and position the close button */
.imgcontainer {
  text-align: center;
  margin: 24px 0 12px 0;
  position: relative;
}

img.avatar {
  width: 40%;
  border-radius: 50%;
}

.container {
  padding: 25px;
}

/* Modal Content/Box */
.modal-content {
  background-color: #fefefe;
  margin: 1% auto 15% auto; /* 5% from the top, 15% from the bottom and centered */
  border: 1px solid #888;
  width: 35%; /* Could be more or less, depending on screen size */
}

/* Add Zoom Animation */
.animate {
  -webkit-animation: animatezoom 0.6s;
  animation: animatezoom 0.6s;
}
</style>
<template>
  <div class="login">
    <h1>Login</h1>
    <div id="id01">
      <form class="modal-content animate">
        <div class="imgcontainer">
          <img src="../assets/logo.png" width="100" height="100" alt="Avatar" class="avatar">
        </div>
        <div class="container">
          <label for="email"><b>Email</b></label>
          <input type="text" v-model="email" placeholder="Enter Email" name="email" required>
          <label for="password"><b>Password</b></label>
          <input type="password" v-model="password" placeholder="Enter Password" name="password" required>
          <button type="button" @click="doLogin">Login</button>
        </div>
        <div class="container" style="background-color:#f1f1f1">
          <span style="float: left">Forgot <a href="/forget-password">password?</a></span>
          <span style="float: right"><a href="/signup">Sign-Up</a></span>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import axios, * as others from 'axios'
export default {
  name: 'Login',
  data: function () {
    return {
      email: '',
      password: '',
      baseUrl: 'http://localhost:8000/api'
    }
  },
  methods: {
    async doLogin() {
      if (this.email === '' || this.password === '') {
        alert('Email and Password is required!')
      } else {
        const response = await axios.post(this.baseUrl + '/login', {
          email: this.email,
          password: this.password
        })
        console.log(response)
        if (response.status === 200) {
          localStorage.setItem('token', JSON.stringify(response.data.data.token))
          localStorage.setItem('auth_user', JSON.stringify(response.data.data.user))
          await this.$router.push({ path: '/home' })
        } else if (response.status === 401) {
          alert('Invalid credentials!')
        } else {
          alert('Something went wrong!')
        }
      }
    }
  }
}
</script>
