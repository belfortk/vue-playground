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
    <hr>
    <h2> Message:</h2>
    <h3> {{ message }} </h3>

  </div>
</template>

<script>
export default {
  name: 'test',
  props: {
    message: {
      default: 'test message',
      type: String
    }
  },
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
input{
  margin-bottom: 1rem;
}
</style>
