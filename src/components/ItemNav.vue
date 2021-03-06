<template>
  <div>
    <li @click="$emit('toggle-chart')">
      <span> {{label}} </span>
    </li>
  </div>
</template>

<script>
export default {
  name: "ItemNav",
  props: {
    label: String,
  },
  emmits: ["toggle-chart"],
};
</script>

<style scoped>
li {
  padding: 5px;
  cursor: pointer;
  font-size: 1.2rem;
  text-align: center;
  list-style: none;
}

li:hover {
  border-bottom: 2px solid #276678;
}
</style>