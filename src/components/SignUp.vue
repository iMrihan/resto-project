<template>
  <img class="logo" src="../assets/pngwing.com.png" alt="" />
  <h1>Sign Up</h1>
  <div class="register">
    <input type="text" placeholder="Enter Name" v-model="name" />

    <input type="email" placeholder="Enter Email" v-model="email" />

    <input type="password" placeholder="Enter password" v-model="password" />
    <button v-on:click="signup">Sign Up</button>
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
      console.log("result", result);
      if (result.status === 201) {
        alert("Sign Up Done");
      }
      localStorage.setItem("user-info", JSON.stringify(result.data));
    },
  },
};
</script>

<style>
.logo {
  width: 100px;
}

.register input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid skyblue;
}
.register button {
  width: 320px;
  height: 40px;
  border: 1px solid skyblue;
  color: white;
  background-color: skyblue;
  cursor: pointer;
}
</style>
