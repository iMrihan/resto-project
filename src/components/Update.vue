<template>
  <Header />
  <h1>Hello {{ user }}, Welcome On Update Restaurant Page</h1>

  <form class="update">
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
    <button type="button" v-on:click="updateRestaurant">
      Update Restaurant
    </button>
  </form>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
  name: "Update",
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
    async updateRestaurant() {
      let result = await axios.put(
        `http://localhost:3000/restaurants/${this.$route.params.id}`,
        this.restaurant
      );
      if (result.status == 200) {
        this.$router.push({ name: "Home" });
      }
    },
  },
  async mounted() {
    let { data } = await axios.get(
      `http://localhost:3000/restaurants/${this.$route.params.id}`
    );

    this.restaurant = data;

    let user = localStorage.getItem("user-info");
    this.user = JSON.parse(user).name;

    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>

<style></style>
