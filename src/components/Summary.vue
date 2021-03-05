<template>
  <div id="wrapper" v-if="toggleVisibility">
    <h2>Resumen</h2>
    <hr />
    <p>Registros esperados: {{ searchResult[1]*2 }}</p>
    <p>Registros actuales: {{ searchResult[1] }}</p>
    <p>Registros faltantes: {{ searchResult[1] }}</p>
  </div>
</template>

<script>
export default {
  name: "Summary",
  props: ["searchResult", "toggleVisibility"],
};
</script>

<style scoped>
h2 {
  text-align: center;
  font-size: 1.2rem;
}
p {
  font-size: 0.8rem;
}

.wrapper {
  margin: auto;
  width: 20%;
}

@media all and (min-width: 600px) {
  h2 {
    font-size: 1.6rem;
  }
  p {
    font-size: 1.2rem;
  }
}
</style> 