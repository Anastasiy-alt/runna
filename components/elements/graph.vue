<script setup>
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend
} from 'chart.js'
import { Line } from 'vue-chartjs'

const props = defineProps([
    'graph',
])
ChartJS.register(
    CategoryScale,
    LinearScale,
    PointElement,
    LineElement,
    Title,
    Tooltip,
    Legend
)
const data = {
  labels: props.graph.labels,
  datasets: [
    {
      borderColor: '#EF3124',
      pointBackgroundColor: '#EF3124',
      pointBorderColor: '#fff',
      data: props.graph.data,
      tension: 0.3
    }
  ]
}
const options = {
  locale: 'ru-RU',
  plugins: {
    legend: {
      display: false,
    }
  },
  responsive: false,
  maintainAspectRatio: false
}
</script>

<template>
  <Line class="graph" :data="data" :options="options" />
</template>

<style lang="sass">
.graph
  width: 100%
  height: 322px

</style>