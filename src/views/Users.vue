<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <div class="about">
      <h1 class="mt-3">Users Page</h1>
    </div>
  </div>
</template>

<script>
import { collapsed, toggleSidebar } from '@/components/sidebar/state'
import Sidebar from '@/components/sidebar/Sidebar.vue'
import { sidebarWidth } from '@/components/sidebar/state'

export default {
  components: {
    Sidebar
  },
  setup() {
    return { collapsed, toggleSidebar, sidebarWidth }
  }
}
</script>
