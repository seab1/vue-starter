<template>
  <div id>
    <h1>Welcome to the login system</h1>
    <div v-if="loggedIn != 'nobody'">
      <h2> Bonjour, {{ email }} </h2>
      <p @click="logout()" style="color:blue;"> Wyloguj </p>
    </div>

    <div v-else>
      <input type="email" v-model="email">
      <button @click="sayBonjour()">Wchodze</button>
    </div>
  </div>
</template>

<script>
import "milligram";

export default {
  data() {
    return {
      email: '',
      loggedIn: 'nobody'
  };
  },

  methods:
  {
    sayBonjour()
    {
      this.loggedIn = this.email;
    },

    logout()
    {
      this.loggedIn = 'nobody';
      this.email = '';
    }
  }
}


</script>

<style>

</style>
