<template>
  <Header />
  <h1>Hello User, Welcome on Add Resturant Page</h1>
  <form class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="resturant.name">
    <input type="text" name="address" placeholder="Enter Address" v-model="resturant.address">
    <input type="text" name="contact" placeholder="Enter Contact" v-model="resturant.contact">
    <button type="button" @click="addResturant">Add new Resturant</button>
  </form>
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Add",
  data() {
    return {
      resturant: {
        name: '',
        address: '',
        contact: ''
      }
    }
  },
  methods: {
    async addResturant() {
      const result = await axios.post("http://localhost:3000/resturants", {
        name: this.resturant.name,
        address: this.resturant.address,
        contact: this.resturant.contact
      });
      if(result.status == 201) {
        this.$router.push({name: 'Home'})
      }
    }
  },
  components: {
    Header
  },
  mounted() {
    let user = localStorage.getItem('user-info');
    if(!user) {
      this.$router.push({name: 'SignUp'})
    }
  }
}
</script>