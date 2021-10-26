<template>
  <div class="card">
    <h2>Added food</h2>
    <!-- <button @click="loadData">Load data</button> -->
    <ul>
      <li :class="{alert: food.difference <=2 && food.difference >0, expired: food.difference<0}" v-for="food in foods" :key="food.id">
        <p>{{ food.name }}</p>
        <p>Data waznosci: {{ food.expirationDate }}</p>
        <button @click="deleteFood(food.id)" class="deleteButton">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      foods: [],
    };
  },
  methods: {
    calcuteDaysToExpire(food){
      const actualDate = new Date();
      const expireDate = new Date(food.expirationDate);
      const difference = (expireDate.getTime() - actualDate.getTime()) / (1000 * 3600 * 24);
      console.log(difference);
      console.log(difference <= 2);
      return difference;
    },
    loadData() {
      fetch(
        "https://food-expiration-app-default-rtdb.europe-west1.firebasedatabase.app/foods.json"
      )
        .then((response) => {
          if (response.ok) {
            return response.json();
          }
        })
        .then((data) => {
          console.log(data);
          let results = [];
          for (const id in data) {
            results.push({
              id: id,
              name: data[id].name,
              expirationDate: data[id].expirationDate,
              difference: this.calcuteDaysToExpire(data[id])
            });
          }
          results.sort(function(a,b){
            return new Date(a.expirationDate) - new Date(b.expirationDate);
          })
          this.foods = results;
        });
    },
    deleteFood(id){
      const output = this.foods.filter((food) => food.id !== id);
      fetch(
        "https://food-expiration-app-default-rtdb.europe-west1.firebasedatabase.app/foods/"+ id +".json"
      ,{
        method: "DELETE",
        headers: {
          'Content-Type': 'application/json'
        }
      })
      this.foods = output;
    }
  },
  mounted(){
    this.loadData();
  }
};
</script>

<style scoped>
.card li {
  color: white;
  background-color: rgb(80, 167, 85);
  width: 500px;
  margin-left: auto;
  margin-right: auto;
  border-radius: 24px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  margin-top: 30px;
  padding: 5px 0;
  list-style: none;
}
.alert{
  background-color: rgb(230, 175, 93) !important;
}
.expired{
  background-color: rgb(230, 93, 93) !important;
}
.deleteButton{
  border: none;
  background: none;
  color: white;
  cursor: pointer;
}
</style>