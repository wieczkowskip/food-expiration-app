<template>
  <div class="head">
    <h2>Add new food</h2>
  </div>
  <div class="form">
    <form @submit.prevent="sendData">
      <div class="form-item">
        <label for="FoodName">Food name: </label>
        <input type="text" name="FoodName" v-model="FoodName" />
      </div>

      <div class="form-item">
        <label for="FoodExpirationDate">Food expiration date: </label>
        <input
          type="date"
          name="FoodExpirationDate"
          v-model="FoodExpirationDate"
        />
      </div>
      <button>Add
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      FoodName: '',
      FoodExpirationDate: null
    };
  },
  methods: {
    sendData() {
      fetch('https://food-expiration-app-default-rtdb.europe-west1.firebasedatabase.app/foods.json', {
        method: 'POST',
        headers:{
          'Content-Type': 'application/json',
        },
        body: JSON.stringify({
          id: new Date().toISOString(),
          name: this.FoodName,
          expirationDate: this.FoodExpirationDate
        }),
      });
      this.FoodName = '';
      this.FoodExpirationDate = null;
    },
  },
};
</script>

<style scoped>
.head {
  color: white;
  background-color: rgb(36, 128, 90);
  border-radius: 24px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  padding: 10px;
  margin: 10px;
}
.form {
  color: white;
  background-color: rgb(48, 202, 138);
  border-radius: 24px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  margin: 10px;
  margin-left: auto;
  margin-right: auto;
  text-align: center;
  width: 600px;
  padding: 20px;
}
.form-item{
  margin: 10px;
}

input[type="text"],
input[type="date"] {
  background-color: rgb(255, 255, 255);
  border: none;
  width: 200px;
  height: 20px;
  margin: 1px;
}
</style>