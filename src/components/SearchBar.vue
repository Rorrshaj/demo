<template>
  <div class="container">
    <input
      class="searchBar"
      placeholder="Buscar por región"
      @keyup="$emit('search-data', search)"
      v-model="search"
      type="text"
    />
  </div>
</template>

<script>
export default {
  name: "SearchBar",
  data() {
    return {
      search: "",
    };
  },
  emmits: ["search-data"],
};
</script>

<style scoped>
.container {
  width: 50vw;
  margin: auto;
  text-align: center;
}
.searchBar {
  font-family: "Roboto", sans-serif;
  border: #2e2e31 2px solid;
  border-radius: 15px;
  background-color: #fcfaff;
  padding: 5px 10px;
  width: 150px;
  text-align: center;
  outline: none;
}
</style>