<template>
  <button @click="$emit('btn-toggle')">+</button>
</template>

<script>
export default {
  data() {
    return {};
  },
  emmits: ["btn-toggle"],
};
</script>

<style scoped>
button {
  position: absolute;
  right: 40px;
  top: 50px;
  font-weight: bolder;
  padding: 5px 8px;
  outline: none;
  border: solid #000000 2px;
  font-size: 0.8rem;
  background-color: transparent;
}
@media all and (min-width: 600px) {
  button {
      font-size: 1.2rem;
  }
}
</style>