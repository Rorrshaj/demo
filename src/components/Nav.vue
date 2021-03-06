<template>
  <div class="nav-container">
    <ItemNav @toggle-chart="$emit('toggle-chart')" v-for="label in labels" :key="label" :label="label"/>
    <SearchBar @search-data="searchData" />
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
      labels: ['Regiones +'],
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
  align-items: center;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-evenly;
  padding: 30px 0 0 0;
  position: fixed;
  top: 0;
  width: 100vw;
}
</style>