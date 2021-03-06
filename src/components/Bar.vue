<template>
  <div class="bar-wrapper">
    <h1>Avance general</h1>
    <canvas id="bar-chart"></canvas>
  </div>
</template>

<script>
import Chart from "chart.js";

export default {
  name: "Bar",
  props: {
    generalData: Map,
  },
  data() {
    return {
      chartData: {
        type: "horizontalBar",
        data: {
          labels: [...this.generalData.keys()],
          datasets: [
            {
              data: [...this.generalData.values()],
              backgroundColor: [
                "#B776FA",
                "#8268DE",
                "#8086F5",
                "#688DDE",
                "#76C2FA",
                "#6CFAEC",
                "#5FDEAD",
                "#76F5A0",
                "#5FDE66",
                "#95FA6C",
                "#CCFA5D",
                "#DEDC52",
                "#F5E567",
                "#DEBF52",
                "#FAC85D",
                "#FAC05A",
                "#DE9950",
                "#F59A65",
                "#DE6F50",
                "#FA665A",
              ],
              borderColor: [],
              borderWidth: 0,
            },
          ],
        },
        options: {
          scales: {
            yAxes: [
              {
                ticks: {
                  beginAtZero: true,
                },
                gridLines: {
                  display: false,
                },
              },
            ],
            xAxes: [
              {
                gridLines: {
                  display: false,
                },
              },
            ],
          },
          legend: {
            display: false,
          },
          responsive: true,
          maintainAspectRatio: false,
        },
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
    this.createChart("bar-chart", this.chartData);
  },
};
</script>

<style scoped>
h1 {
  font-size: 1.6rem;
}

.bar-wrapper {
  display: flex;
  flex-flow: column;
  align-items: center;
  justify-content: center;
  margin: 50px auto 0;
  height: 500px;
  width: 70%;
}
</style>