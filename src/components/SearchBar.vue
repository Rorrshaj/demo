<template>
  <div class="search-container">
    <input
      class="search-bar"
      placeholder="Buscar por región"
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
.search-bar {
  border: 2px solid;
  border-radius: 20px;
  background-color: transparent;
  font-family: "Roboto", sans-serif;
  font-size: 1rem;
  outline: none;
  padding: 8px 12px;
  text-align: center;
  width: 150px;
}
</style>