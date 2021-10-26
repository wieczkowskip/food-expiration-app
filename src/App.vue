<template>
  <button @click="changeMode('ShowFood')">Show Food</button>
  <button @click="changeMode('AddFood')">Add Food</button>
  <component :is="cmpName"></component>
</template>

<script>
import ShowFood from "./components/ShowFood.vue";
import AddFood from './components/AddFood.vue';
export default {
  name: "App",
  components: {
    ShowFood,
    AddFood
  },
  data() {
    return {
      cmpName: "ShowFood",
    };
  },
  methods: {
    changeMode(mode) {
      this.cmpName = mode;
    },
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
  margin-top: 60px;
}
</style>
