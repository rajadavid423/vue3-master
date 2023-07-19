<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <h1>The sidebar is {{ collapsed ? 'closed' : 'open' }}</h1>
    <div>
      <button class="form-control btn-secondary btn-sm" @click="toggleSidebar">Toggle Sidebar</button>
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
