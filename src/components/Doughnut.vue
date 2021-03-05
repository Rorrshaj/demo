<template>
  <div class="chart-wrapper">
    <h1>{{ searchResult[0] }}</h1>
    <canvas id="chart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js";

export default {
  name: "Doughnut",
  props: {
    searchResult: Array,
  },
  data() {
    return {
      chartData: {
        type: "doughnut",
        data: {
          labels: ["Actual", "Esperado"],
          datasets: [
            {
              data: [this.searchResult[1], this.searchResult[1] * 2],
              backgroundColor: ["#ffbe0f", "#fa1e0e"],
              borderWidth: 3,
            },
          ],
        },
        options: {},
      },
    };
  },
  methods: {
    createChart(chartId, chartData) {
      const ctx = document.getElementById(chartId);
      const myChart = new Chart(ctx, {
        type: chartData.type,
        data: chartData.data,
        options: chartData.options,
      });
    },
  },
  mounted() {
    this.createChart("chart", this.chartData);
  },
};
</script>

<style scoped>
h1 {
  font-size: 1.6rem;
}

.chart-wrapper {
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: center;
  width: 100%;
}

@media all and (min-width: 600px) {
  h1 {
    font-size: 2.2rem;
  }
  .chart-wrapper {
    width: 70%;
  }
}
</style>