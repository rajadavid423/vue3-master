<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <h1>Dashboard</h1>
    <div class="container mt-5">
      <div class="row">
        <div class="col-md-4 col-xl-3">
          <div class="card bg-c-blue order-card">
            <div class="card-block mt-3">
              <h6 class="m-b-20">Orders Received</h6>
              <h2><i class="fa fa-cart-plus f-left"></i><span class="ms-3">486</span></h2>
              <p class="m-b-0">Completed Orders<span class="f-right ms-2">351</span></p>
            </div>
          </div>
        </div>

        <div class="col-md-4 col-xl-3">
          <div class="card bg-c-green order-card">
            <div class="card-block mt-3">
              <h6 class="m-b-20">Orders Received</h6>
              <h2><i class="fa fa-rocket f-left"></i><span class="ms-3">486</span></h2>
              <p class="m-b-0">Completed Orders<span class="f-right ms-2">351</span></p>
            </div>
          </div>
        </div>

        <div class="col-md-4 col-xl-3">
          <div class="card bg-c-yellow order-card">
            <div class="card-block mt-3">
              <h6 class="m-b-20">Orders Received</h6>
              <h2><i class="fa fa-oil-can f-left"></i><span class="ms-3">486</span></h2>
              <p class="m-b-0">Completed Orders<span class="f-right ms-2">351</span></p>
            </div>
          </div>
        </div>

        <div class="col-md-4 col-xl-3">
          <div class="card bg-c-pink order-card">
            <div class="card-block mt-3">
              <h6 class="m-b-20">Orders Received</h6>
              <h2><i class="fa fa-credit-card f-left"></i><span class="ms-3">486</span></h2>
              <p class="m-b-0">Completed Orders<span class="f-right ms-2">351</span></p>
            </div>
          </div>
        </div>
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
