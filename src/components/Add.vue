<template>
  <Header />
  <h1>Hello {{ user }}, Welcome On Add Restaurant Page</h1>
  <form class="add">
    <input
      type="text"
      placeholder="Enter Name"
      v-model="restaurant.name"
      name="name"
    />
    <input
      type="text"
      placeholder="Enter Address"
      v-model="restaurant.address"
      name="address"
    />

    <input
      type="text"
      placeholder="Enter Contact"
      v-model="restaurant.contact"
      name="contact"
    />
    <button type="button" v-on:click="addRestaurant">Add New Restaurant</button>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";

export default {
  name: "Add",
  components: {
    Header,
  },
  data() {
    return {
      restaurant: {
        name: "",
        address: "",
        contact: "",
      },
      user: "",
    };
  },
  methods: {
    async addRestaurant() {
      let result = await axios.post(
        "http://localhost:3000/restaurants",
        this.restaurant
      );
      console.log("test:", result);
      if (result.status == 201) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    this.user = JSON.parse(user).name;
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
