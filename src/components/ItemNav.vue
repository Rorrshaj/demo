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
  padding: 5px 0;
  cursor: pointer;
  font-size: 1.2rem;
  text-align: center;
  list-style: none;
  border-top: solid #ffffff 2px;
  border-bottom: solid #ffffff 2px;
}

li span {
  color: #276678;
}

li:hover {
  background-color: #b6cbdb;
}
</style>