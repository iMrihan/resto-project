<template>
  <div class="nav">
    <a href="home">Home</a>
    <a href="home">Add Restaurant</a>
    <a href="home">Update Restaurant</a>
    <a href="home">Logout</a>
  </div>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style>
.nav {
  background: #333;
  overflow: hidden;
}
.nav a {
  float: left;
  color: #f2f2f2;
  text-align: center;
  padding: 10px 16px;
  text-decoration: none;
  font-size: 16px;
  margin-right: 4px 5px;
}
.nav a:hover {
  background: #ddd;
  color: #222;
}
</style>
