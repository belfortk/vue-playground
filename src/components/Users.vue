<template>
  <div id="users">
    <h1> Users</h1>
    <form v-on:submit="addUser">
      <input type="text" v-model="newUser.name" class="user-input" placeholder="Enter Name">
      <br>
      <input type="text" v-model="newUser.email" class="user-input" placeholder="Enter Email">
      <br>
      <input type="submit" value="Submit">
    </form>
    
    <br>
    <br>
    <ul>
      <li v-for="(user, i) in users" v-bind:key="`user-${i}`">
        <input type="checkbox" class="toggle" v-model="user.contacted">
        <span :class="{contacted: user.contacted }">
        {{ user.name }}:  {{ user.email }} <button v-on:click="deleteUser(i)">X</button>
        </span>
      </li>
    </ul>
  </div>
  
</template>


<script>
import axios from 'axios';
export default {
  name: 'users',
  data() {
    return {
      newUser: {},
      users: [],
    };
  },
  created: function(){
    // this.$http.get('https://jsonplaceholder.typicode.com/users')
    // .then(res => {
    //   this.users = res.data
    // });
    axios.get('https://jsonplaceholder.typicode.com/users')
    .then(res => {
      this.users = res.data
    });
  },
  methods: {
    addUser:  function(e){
      e.target.reset();
      this.users.push({
        name: this.newUser.name,
        email: this.newUser.email,
        contacted: this.newUser.contacted
      })
      this.newUser = {};
      e.preventDefault();

    },
    deleteUser: function(index){
      this.users.splice(index, 1);
    }
  }
};
</script>


<style scoped>
  ul {
    list-style-type: none;
  }

  .contacted{
    text-decoration: line-through; 
  }
</style>


