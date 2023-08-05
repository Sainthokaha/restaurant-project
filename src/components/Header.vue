<template>
  <div class="nav">
    <router-link to="/home">Home</router-link>
    <router-link to="/add">Add Resturant</router-link>
    <a v-on:click="logout" href="#">Logout</a>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Header',
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push({name: 'Login'})
    }
  }
}
</script>

<style>
  .nav {
    background-color: #333;
    overflow: hidden;
  }

  .nav a {
    float: left;
    color: #f2f2f2;
    padding: 14px 16px;
    text-align: center;
    font-size: 17px;
    text-decoration: none;
    margin-right: 5px;
  }

  .nav a:hover {
    background-color: #ddd;
    color: #333;
  }
</style>