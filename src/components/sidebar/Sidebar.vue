<script>
import SidebarLink from './SidebarLink'
import { collapsed, toggleSidebar, sidebarWidth } from './state'
import axios from 'axios'

export default {
  props: {},
  components: { SidebarLink },
  setup() {
    return { collapsed, toggleSidebar, sidebarWidth }
  },
  data() {
    return {
      isAuthorized: false,
      authUserName: '',
      baseUrl: 'http://localhost:8000/api'
    }
  },
  mounted() {
    let token = JSON.parse(localStorage.getItem('token'))
    if (token && token !== '') {
      let user = JSON.parse(localStorage.getItem('auth_user'))
      this.isAuthorized = true
      this.authUserName = user.name
    }
  },
  methods: {
    async doLogout() {
      let token = JSON.parse(localStorage.getItem('token'))
      const headers = {
        Authorization: 'Bearer ' + token,
        'My-Custom-Header': 'foobar'
      }
      const response = await axios.get(this.baseUrl + '/logout', { headers })
      console.log(response)
      if (response.status === 200) {
        localStorage.removeItem('token')
        localStorage.removeItem('auth_user')
        await this.$router.push({ path: '/login' })
      } else if (response.status === 401) {
        alert('Invalid credentials!')
        await this.$router.push({ path: '/login' })
      } else {
        alert('Something went wrong!')
        await this.$router.push({ path: '/login' })
      }
    }
  }
}
</script>

<template>
  <div class="sidebar" :style="{ width: sidebarWidth }">
    <h1>
      <span v-if="collapsed">V</span>
      <span v-else><h2>Vue Sidebar</h2></span>
    </h1>
    <h3 v-if="isAuthorized && !collapsed">
      <span>
        <h4>Welcome {{ authUserName }}!</h4>
      </span>
    </h3>

    <SidebarLink to="/home" icon="fas fa-home">Home</SidebarLink>
    <SidebarLink to="/dashboard" icon="fas fa-columns">Dashboard</SidebarLink>
    <SidebarLink to="/analytics" icon="fas fa-chart-bar">Analytics</SidebarLink>
    <SidebarLink to="/users" icon="fas fa-users">Users</SidebarLink>
    <SidebarLink to="/about" icon="fas fa-book-reader">About</SidebarLink>
    <SidebarLink to="/profile" icon="fas fa-user">Profile</SidebarLink>
    <br />
    <span @click="doLogout" class="float-start me-5"><i class="fas fa-power-off me-3"></i>Logout</span>

    <span
      class="collapse-icon"
      :class="{ 'rotate-180': collapsed }"
      @click="toggleSidebar"
    >
      <i class="fas fa-angle-double-left" />
    </span>
  </div>
</template>

<style>
:root {
  --sidebar-bg-color: #2f855a;
  --sidebar-item-hover: #38a169;
  --sidebar-item-active: #276749;
}
</style>

<style scoped>
.sidebar {
  color: white;
  background-color: var(--sidebar-bg-color);

  float: left;
  position: fixed;
  z-index: 1;
  top: 0;
  left: 0;
  bottom: 0;
  padding: 0.5em;

  transition: 0.3s ease;

  display: flex;
  flex-direction: column;
}

.sidebar h1 {
  height: 1em;
}

.collapse-icon {
  position: absolute;
  bottom: 0;
  padding: 0.75em;

  color: rgba(255, 255, 255, 0.7);

  transition: 0.2s linear;
}

.rotate-180 {
  transform: rotate(180deg);
  transition: 0.2s linear;
}
</style>
