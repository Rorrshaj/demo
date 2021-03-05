<template>
  <div id="app">
    <div id="nav">
      <!--
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> 
      -->
    </div>
    <router-view />
  </div>
</template>

<style>
body {
  margin: 0;
  padding: 0;
  background-color: #faf9fd;
}

#app {
  font-family: "Roboto", sans-serif;
  color: #979696;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  padding: 0px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
