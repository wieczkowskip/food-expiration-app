<template>
  <div class="head">
    <h2>Add new food</h2>
  </div>
  <submit-error v-if="sendError"></submit-error>
  <div class="form">
    <form @submit.prevent="sendData">
      <div class="form-item">
        <label for="FoodName">Food name: </label>
        <input
          type="text"
          name="FoodName"
          @blur="checkNameError"
          v-model="FoodName"
        />
        <p class="error" v-if="nameError || sendError">
          {{ errorMessage }}
        </p>
      </div>

      <div class="form-item">
        <label for="FoodExpirationDate">Food expiration date: </label>
        <input
          type="date"
          name="FoodExpirationDate"
          v-model="FoodExpirationDate"
          @blur="checkDateError"
        />
        <p
          class="error"
          v-if="FoodExpirationDate === null && (dateError || sendError)"
        >
          Please set expiration date.
        </p>
      </div>
      <div class="form-item"><button>Add</button></div>
    </form>
  </div>
</template>

<script>
import SubmitError from "./SubmitError.vue";
export default {
  components: {
    SubmitError,
  },
  data() {
    return {
      FoodName: "",
      FoodExpirationDate: null,
      nameError: false,
      dateError: false,
      sendError: false,
    };
  },
  computed: {
    errorMessage() {
      if (this.FoodName.trim() === "") {
        return "Food name can't be empty.";
      } else if (
        !/^[a-zA-Z0-9%ąćęłńóśźżĄĆĘŁŃÓŚŹŻ\s]+$/.test(this.FoodName.trim())
      ) {
        return "Food name can only have letters (PL support), numbers, spaces and %";
      } else return "";
    },
  },
  methods: {
    checkNameError() {
      this.nameError = true;
    },
    checkDateError() {
      this.dateError = true;
    },
    sendData() {
      if (
        this.FoodName.trim() !== "" &&
        /^[a-zA-Z0-9%ąćęłńóśźżĄĆĘŁŃÓŚŹŻ\s]+$/.test(this.FoodName.trim()) &&
        this.FoodExpirationDate !== null
      ) {
        fetch(
          "https://food-expiration-app-default-rtdb.europe-west1.firebasedatabase.app/foods.json",
          {
            method: "POST",
            headers: {
              "Content-Type": "application/json",
            },
            body: JSON.stringify({
              id: new Date().toISOString(),
              name: this.FoodName,
              expirationDate: this.FoodExpirationDate,
            }),
          }
        );
        this.FoodName = "";
        this.FoodExpirationDate = null;
        this.nameError = false;
        this.dateError = false;
        this.sendError = false;
      } else {
        this.sendError = true;
        //alert('Send data error! Please check your data in form.');
      }
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
  padding: 20px 0;
  margin: 10px;
  width: 500px;
  margin-left: auto;
  margin-right: auto;
}
.form {
  color: white;
  background-color: rgb(48, 202, 138);
  border-radius: 24px;
  box-shadow: 3px 3px 3px rgba(0, 0, 0, 0.26);
  margin: 10px;
  margin-left: auto;
  margin-right: auto;
  text-align: justify;
  width: 500px;
  padding: 20px 0;
}
.form-item {
  margin: 15px 10px;
  padding-left: 20px;
}

input[type="text"],
input[type="date"],
button {
  background-color: rgb(255, 255, 255);
  border: none;
  width: 200px;
  height: 20px;
  margin: 1px;
}
button:hover {
  cursor: pointer;
}
.error {
  color: rgb(212, 38, 14);
}
</style>