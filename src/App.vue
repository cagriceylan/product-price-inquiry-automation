<template>
  <div id="app">
    <BaseMenu />
    <img alt="Vue logo" src="./assets/UK.png" />
    <BaseSearchArea msg="..." />
    <BaseListArea />
  </div>
</template>

<script>
import BaseSearchArea from "./components/BaseSearchArea.vue";
//import BaseListArea from "./components/BaseListArea.vue";
import BaseMenu from "./components/BaseMenu.vue";

export default {
  name: "App",
  components: {
    BaseMenu,
    BaseSearchArea,
    //BaseListArea,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.table .thead-dark th {
  color: #fff;
  background-color: #343a40;
  border-color: #454d55;
}
</style>
