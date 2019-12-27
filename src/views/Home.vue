<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <ul>
      <li v-for="user in users" :key="user.name">
        {{ user.name }}
      </li>
    </ul>
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
  }
}
</script>
