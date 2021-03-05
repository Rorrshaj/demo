<template>
  <div class="wrapper">
    <div class="container">
      <Button @btn-toggle="btnToggle" />
      <Bar v-if="toggle" :generalData="jsonData" />
    </div>
    <SearchBar @search-data="searchData" />
    <div class="doughnut-chart">
      <Doughnut v-if="updateChart" :searchResult="searchResult" />
      <Summary :searchResult="searchResult" :toggleVisibility="updateChart" />
    </div>
  </div>
</template>

<script>
import * as Data from "../../db.json";

import SearchBar from "../components/SearchBar.vue";
import Button from "../components/Button.vue";
import Doughnut from "../components/Doughnut.vue";
import Bar from "../components/Bar.vue";
import Summary from "../components/Summary.vue";

export default {
  name: "Home",
  components: {
    SearchBar,
    Button,
    Doughnut,
    Summary,
    Bar,
  },
  data() {
    return {
      jsonData: new Map(),
      searchResult: [],
      generalData: [],
      updateChart: false,
      toggle: false,
    };
  },
  methods: {
    loadData() {
      var arr = Data.default.voters;
      this.jsonData = arr.reduce(
        (count, obj) => count.set(obj.Region, (count.get(obj.Region) || 0) + 1),
        new Map()
      );
    },
    searchData(search) {
      var res = [...this.jsonData.keys()].findIndex(
        (item) => search.toLowerCase() === item.toLowerCase()
      );
      if (res !== -1) {
        this.searchResult = [...this.jsonData.entries()][res];
        this.updateChart = true;
      } else {
        this.updateChart = false;
      }
    },
    btnToggle() {
      this.toggle = !this.toggle;
    },
  },
  mounted() {
    this.loadData();
  },
};
</script>

<style scoped>
.wrapper {
  margin: 50px 0 50px 0;
}

.container {
  width: 80vw;
  margin: 50px auto 0;
}

.doughnut-chart {
  display: flex;
  flex-flow: row wrap;
  align-items: center;
  justify-content: center;
  width: 80vw;
  margin: 0 auto;
}

@media all and (min-width: 800px) {
  .doughnut-chart {
    justify-content: start;
  }
}
</style>