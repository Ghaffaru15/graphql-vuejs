<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <ul>
      <li v-for="user in users" :key="user.name">
        {{ user.name }}
      </li>
    </ul>

    <button @click="createUser">Create User</button>
  </div>
</template>

<script>

import gql from 'graphql-tag'

export default {
  name: 'home',
  data() {
    return {
      users:[],
      user: null
    }
  },
  components: {
  
  },
  apollo: {
    users: gql`query{
      users {
        name
        email
      }
    }`
  },
  methods: {
    createUser() {
      this.$apollo.mutate({
        mutation: gql`mutation {
          createUser(name: "Nafi",email: "nafisa@gmail.com",password: "password") {
            name
            email
          }
        }`
      })
    }
  }
}
</script>
