<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <div class="home">
      <img alt="Vue logo" src="../assets/logo.png" />
      <HelloWorld msg="Welcome to Your Vue.js App" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Sidebar from '@/components/sidebar/Sidebar'
import { sidebarWidth } from '@/components/sidebar/state'
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'Home',
  components: {
    Sidebar,
    HelloWorld
  },
  setup() {
    return { sidebarWidth }
  }
}
</script>
<style>
.home {
  margin-top: 100px;
}
</style>
