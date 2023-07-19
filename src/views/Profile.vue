<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <div class="about">
      <section style="background-color: #fdfcfc;" class="mt-3">
        <h1>Profile Page</h1>
        <div class="container">
          <div class="row mt-5">
            <div class="col-lg-4">
              <div class="card mb-4">
                <div class="card-body text-center">
                  <img src="https://mdbcdn.b-cdn.net/img/Photos/new-templates/bootstrap-chat/ava3.webp" alt="avatar"
                       class="rounded-circle img-fluid" style="width: 150px;">
                  <h5 class="my-3">{{ this.user.name ?? '-' }}</h5>
                  <p class="text-muted mb-1">Full Stack Developer</p>
                  <p class="text-muted mb-4">Bay Area, San Francisco, CA</p>
                  <div class="d-flex justify-content-center mb-2">
                    <button type="button" class="btn btn-primary">Edit</button>
                    <button type="button" class="btn btn-outline-primary ms-1">Change Password</button>
                  </div>
                </div>
              </div>
            </div>
            <div class="col-lg-8">
              <div class="card">
                <div class="card-body">
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">ID</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">{{ this.user.id ?? '-' }}</p>
                    </div>
                  </div>
                  <hr>
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">Full Name</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">{{ this.user.name ?? '-' }}</p>
                    </div>
                  </div>
                  <hr>
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">Email</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">{{ this.user.email ?? '-' }}</p>
                    </div>
                  </div>
                  <hr>
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">Phone</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">{{ this.user.phone ?? '-' }}</p>
                    </div>
                  </div>
                  <hr>
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">DOB</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">{{ this.user.dob ?? '-' }}</p>
                    </div>
                  </div>
                  <hr>
                  <div class="row">
                    <div class="col-sm-3">
                      <p class="mb-0">Address</p>
                    </div>
                    <div class="col-sm-9">
                      <p class="text-muted mb-0">Bay Area, San Francisco, CA</p>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import { collapsed, toggleSidebar } from '@/components/sidebar/state'
import Sidebar from '@/components/sidebar/Sidebar.vue'
import { sidebarWidth } from '@/components/sidebar/state'
import axios from 'axios'

export default {
  components: {
    Sidebar
  },
  setup() {
    return { collapsed, toggleSidebar, sidebarWidth }
  },
  data() {
    return {
      user: '',
      baseUrl: 'http://localhost:8000/api'
    }
  },
  async mounted() {
    let token = JSON.parse(localStorage.getItem('token'))
    const headers = {
      Authorization: 'Bearer ' + token,
      'My-Custom-Header': 'foobar'
    }
    const response = await axios.get(this.baseUrl + '/profile', { headers })
    console.log(response)
    if (response.status === 200) {
      this.user = response.data.data
    }
  }
}
</script>
