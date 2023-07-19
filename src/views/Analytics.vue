<template>
  <Sidebar />
  <div :style="{ 'margin-left': sidebarWidth }">
    <div class="about">
      <h1>Analytics Page</h1>
      <DoughnutChart :chartData="testData" />
    </div>
  </div>
</template>

<script>
import { collapsed, toggleSidebar } from '@/components/sidebar/state'
import Sidebar from '@/components/sidebar/Sidebar.vue'
import { sidebarWidth } from '@/components/sidebar/state'
import { DoughnutChart } from 'vue-chart-3'
import { Chart, registerables } from "chart.js"

Chart.register(...registerables)

export default {
  components: {
    Sidebar,
    DoughnutChart
  },
  setup() {
    const testData = {
      labels: ['Paris', 'Nîmes', 'Toulon', 'Perpignan', 'Autre'],
      datasets: [
        {
          data: [30, 40, 60, 70, 5],
          backgroundColor: ['#77ff82', '#dc2433', '#0a4f02', '#48a3ee', '#A5C8ED'],
        }
      ]
    }
    return { collapsed, toggleSidebar, sidebarWidth, testData }
  }
}
</script>
