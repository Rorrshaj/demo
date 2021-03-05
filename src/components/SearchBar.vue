<template>
  <div class="search-container">
    <input
      class="search-bar"
      placeholder="Buscar por municipio"
      @keyup="$emit('search-data', searchText)"
      @keyup.enter="$emit('search-data', searchText)"
      v-model="searchText"
      type="text"
    />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      searchText: "",
    };
  },
  emmits: ["search-data"],
};
</script>

<style scoped>
.search-container {
  margin: 30px 0;
  text-align: center;
}
.search-bar {
  background-color: #f6f5f5;
  border: solid #fff 2px;
  border-radius: 15px;
  font-family: "Roboto", sans-serif;
  outline: none;
  padding: 8px 12px;
  width: 150px;
}
</style>