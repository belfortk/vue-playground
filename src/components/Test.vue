<template>
  <div id="test">
    <h1>
      {{ title }}
    </h1>
    <p v-if="showName"> {{ user.firstName }} {{ user.lastName }}'s Vue App </p>
    <p v-else> This is a Vue App </p>
    <ul>
      <li v-for="(item,i) in items" v-bind:key="`listing-${i}`"> {{ item.title }}</li>
    </ul>
    <input type="text" v-model="greetingMessage">
    <button v-on:click="greet(greetingMessage)"> Say hi!</button>
    <br>
    <button v-on:click="hideName"> Hide Identity </button>
    <hr>
    <h3>Editing for {{ fullName }} </h3>
    <label> First Name:  </label><input type="text" v-model="user.firstName">
    <label> Last Name:  </label><input type="text" v-model="user.lastName">


  </div>
</template>

<script>
export default {
  name: 'test',
  data () {
    return {
      title: 'Hello World',
      greetingMessage: '' ,
      user: {
        firstName: 'Kyle',
        lastName: 'Belfort'
      },
      showName: true,
      items: [
        {
          title: 'Item 1'
        },
           {
          title: 'Item 2'
        },
           {
          title: 'Item 3'
        }
      ]
    }
  },
  methods: {
    greet: function(text){
      let greeting = (text.length > 1) ? text : 'Hello!'
      alert(greeting);
    },
    hideName: function(){
      this.showName = !this.showName;
    }
  },
  computed: {
    fullName: function(){
      return this.user.firstName + ' ' + this.user.lastName; 
    }
  }
}
</script>

<style scoped>
  ul {
  list-style-type: none;
}
</style>
