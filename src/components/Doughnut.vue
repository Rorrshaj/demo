<template>
  <div class="chart-summary">
    <div class="chart-wrapper">
      <h1>{{ searchResult[0] }}</h1>
      <canvas id="chart"></canvas>
    </div>
    <div>
      <h2>Resumen</h2>
      <hr />
      <p>Registros esperados: {{ searchResult[1] * 2 }}</p>
      <p>Registros actuales: {{ searchResult[1] }}</p>
      <p>Registros faltantes: {{ searchResult[1] }}</p>
    </div>
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
              backgroundColor: ["#276678", "#d3e0ea"],
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

h2 {
  text-align: center;
  font-size: 1.4rem;
}
p {
  font-size: 1rem;
}

.chart-summary {
  align-items: center;
  display: flex;
  flex-flow: row wrap;
  justify-content: center;
  text-align: center;
  
}
.chart-wrapper {
  width: 70%;
}
</style>