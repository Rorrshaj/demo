<template>
  <div class="wrapper">
    <Nav @toggle-chart="toggleChart" @search-data="searchData" />
    <div class="chart-container">
      <Bar v-if="toggle" :generalData="jsonData" />
      <Doughnut v-if="updateChart" :searchResult="searchResult" />
    </div>
  </div>
</template>

<script>
import * as Data from "../../db.json";

import Bar from "../components/Bar.vue";
import Doughnut from "../components/Doughnut.vue";
import Nav from "../components/Nav.vue";

export default {
  name: "Home",
  props: {
    inputText: String,
  },
  components: {
    Bar,
    Doughnut,
    Nav,
  },
  data() {
    return {
      jsonData: new Map(),
      generalData: [],
      searchResult: [],
      toggle: false,
      updateChart: false,
    };
  },
  methods: {
    loadData() {
      var data = Data.default.voters;
      this.jsonData = data.reduce(
        (count, obj) => count.set(obj.Region, (count.get(obj.Region) || 0) + 1),
        new Map()
      );
    },
    searchData(search) {
      var result = [...this.jsonData.keys()].findIndex(
        (item) => search.toLowerCase() === item.toLowerCase()
      );
      if (result !== -1) {
        this.searchResult = [...this.jsonData.entries()][result];
        this.updateChart = true;
        this.toggle = false;
      } else {
        this.updateChart = false;
      }
    },
    toggleChart() {
      this.toggle = !this.toggle;
      this.updateChart = false;
    },
  },
  mounted() {
    this.loadData();
  },
};
</script>

<style scoped>
.chart-container {
  margin: 0 0 0 220px;
}
</style>