<template>
  <img class="logo" src="../assets/pngwing.com.png" alt="" />
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" placeholder="Enter Name" v-model="name" />

    <input type="email" placeholder="Enter Email" v-model="email" />

    <input type="password" placeholder="Enter password" v-model="password" />
    <button v-on:click="signup">Sign Up</button>
    <p>
      <router-link to="/login">Login</router-link>
    </p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SingUp",
  data() {
    return {
      name: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signup() {
      let result = await axios.post("http://localhost:3000/users", {
        email: this.email,
        name: this.name,
        password: this.password,
      });
      if (result.status == 201) {
        localStorage.setItem("user-info", JSON.stringify(result.data));
        this.$router.push({ name: "Home" });
      }
    },
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>

<style></style>
