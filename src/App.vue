<template>
  <div id>
    <h1>Welcome to the login system</h1>
    <div v-if="loggedIn != 'nobody'">
      <h2> Bonjour, {{ loggedIn }} </h2>
      <p @click="logout()" style="color:blue;"> Wyloguj </p>
    </div>

    <div v-else>
      <login-form @login="sayBonjour($event)"></login-form>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm"

export default {
  components: {LoginForm},

  data() {
    return {
      loggedIn: 'nobody'
  };
  },

  methods:
  {
    sayBonjour(givenEmail)
    {
      this.loggedIn = givenEmail;
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
