<template>
  <div id="app">
    <personelList />
  </div>
</template>
<script>
import personelList from "./components/PersonelList";
export default {
  data() {
    return {};
  },
  components: {
    personelList,
  },
};
</script>
<style>
*,
*::after,
*::before {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
p {
  margin-bottom: 10px;
}
</style>
