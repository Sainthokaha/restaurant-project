<template>
  <Header />
  <h1>Hello User, Welcome on Update Resturant Page</h1>
  <form class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="resturant.name">
    <input type="text" name="address" placeholder="Enter Address" v-model="resturant.address">
    <input type="text" name="contact" placeholder="Enter Contact" v-model="resturant.contact">
    <button type="button" @click="updateResturant">Update Resturant</button>
  </form>
</template>

<script>
import Header from './Header.vue'
import axios from 'axios';
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Update",
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
    async updateResturant() {
      console.log(this.resturant)
      const result = await axios.put("http://localhost:3000/resturants/" + this.$route.params.id, {
        name: this.resturant.name,
        address: this.resturant.address,
        contact: this.resturant.contact
      });
      if(result.status == 200) {
        this.$router.push({name: 'Home'})
      }
    }
  },
  components: {
    Header
  },
  async mounted() {
    let user = localStorage.getItem('user-info');
    if(!user) {
      this.$router.push({name: 'SignUp'})
    }
    const result = await axios.get('http://localhost:3000/resturants/' + this.$route.params.id)
    this.resturant = result.data;
  }
}
</script>