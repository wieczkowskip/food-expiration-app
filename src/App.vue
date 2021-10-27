<template>
  <button class="mainButton" @click="changeMode('ShowFood')">Show Food</button>
  <button class="mainButton" @click="changeMode('AddFood')">Add Food</button>
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
.mainButton{
  width: 250px;
  border-style: none;
  border-radius: 12px;
  box-shadow: 3px 3px 3px rgba(0,0,0,0.26);
  background-color: rgb(16, 209, 103);
  color: white;
  height: 50px;
}
.mainButton:hover{
  background-color: rgb(11, 146, 72);
  cursor:pointer;
}
.mainButton:focus{
  background-color: rgb(11, 146, 72);
  cursor:default;
}
</style>
