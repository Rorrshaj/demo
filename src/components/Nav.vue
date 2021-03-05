<template>
  <div class="nav-container">
    <SearchBar @search-data="searchData" />
    <ItemNav @toggle-chart="$emit('toggle-chart')" v-for="label in labels" :key="label" :label="label"/>
  </div>
</template>

<script>
import SearchBar from "./SearchBar";
import ItemNav from "../components/ItemNav.vue";

export default {
  name: "Nav",
  components: {
    SearchBar,
    ItemNav,
  },
  data () {
    return {
      labels: ['Regiones'],
    }
  },
  methods: {
    searchData(searchText) {
      this.$emit('search-data', searchText)
    }
  },
  emmits: ['search-data', 'toggle-chart'],
};
</script>

<style scoped>
.nav-container {
  background-color: #d3e0ea;
  height: 100%;
  left: 0;
  position: fixed;
  top: 0;
  width: 220px;
}
</style>