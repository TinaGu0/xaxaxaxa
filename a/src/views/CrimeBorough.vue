<template>
  <div>
    <h1>Crime Type Based on Borough</h1>
    <div>
      <select v-model="selectedBorough" @change="updateChartData">
        <option value="B">Brooklyn</option>
        <option value="S">Staten Island</option>
        <option value="B">Bronx</option>
        <option value="Q">Queens</option>
        <option value="M">Manhattan</option>
      </select>
    </div>
    <div>
      <Pie :data="chartData" :options="options" />
    </div>
  </div>
</template>

<script>
import { Pie } from 'vue-chartjs'
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from 'chart.js'
ChartJS.register(ArcElement, Tooltip, Legend)

export default {
  name: 'CrimeBorough',
  components: { Pie },
  data () {
    return {
      selectedBorough: 'B', // Defaults to Brooklyn
      chartData: {
        labels: ['Murder', 'Steal', 'Home Invasion', 'Shooting'],
        datasets: [
          {
            backgroundColor: ['#41B883', '#E46651', '#00D8FF', '#DD1B16'],
            data: [0, 0, 0, 0]
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false
      }
    }
  },
  mounted() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const result = await fetch('https://data.cityofnewyork.us/resource/uip8-fykc.json');
        const data = await result.json();
        console.log(data);
      } catch (error) {
        console.log(error);
      }
    },
    updateChartData() {
      console.log(this.selectedBorough);
    }
  },
  watch: {
    selectedBorough: 'updateChartData'
  }
}
</script>

<style scoped>
h1 {
  font-family: 'Hind', sans-serif;
  background-color: lightblue;
  margin: 4rem 35rem 1.5rem;
  border-radius: 1rem;
  font-size: 3rem;
}
</style>