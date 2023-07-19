<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <div class="about">
      <h1 class="mt-3">About Page</h1>
      <div class="container-fluid">
        <b-skeleton-wrapper>
          <b-card>
            1. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien,
            non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie,
            massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est.
            Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac
            turpis egestas. Phasellus at consequat dui. Aenean tristique sagittis quam,
            sit amet sollicitudin neque sodales in.
          </b-card>
          <br>
          <br>
          <b-card>
            2. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien,
            non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie,
            massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est.
            Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac
            turpis egestas. Phasellus at consequat dui. Aenean tristique sagittis quam,
            sit amet sollicitudin neque sodales in.
          </b-card>
          <br>
          <br>
          <b-card>
            3. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien,
            non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie,
            massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est.
            Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac
            turpis egestas. Phasellus at consequat dui. Aenean tristique sagittis quam,
            sit amet sollicitudin neque sodales in.
          </b-card>
          <br>
          <br>
          <b-card>
            4. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien,
            non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie,
            massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est.
            Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac
            turpis egestas. Phasellus at consequat dui. Aenean tristique sagittis quam,
            sit amet sollicitudin neque sodales in.
          </b-card>
          <br>
          <br>
          <b-card>
            5. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas viverra nunc sapien,
            non rhoncus elit tincidunt vitae. Vestibulum maximus, ligula eu feugiat molestie,
            massa diam imperdiet odio, vitae viverra ligula est id nisi. Aliquam ut molestie est.
            Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac
            turpis egestas. Phasellus at consequat dui. Aenean tristique sagittis quam,
            sit amet sollicitudin neque sodales in.
          </b-card>
        </b-skeleton-wrapper>
      </div>
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
