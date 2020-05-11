<template>
  <div id>
    <h1>Welcome to the login system</h1>
    <div v-if="loggedIn != 'nobody'">
      <h2> Bonjour, {{ loggedIn }} </h2>
      <p @click="logout()" style="color:blue;"> Log out </p>
      <meeting-page></meeting-page>
    </div>

    <div v-else>
      <login-form @login="sayBonjour($event)"></login-form>
    </div>
  </div>
</template>

<script>
import "milligram";
import LoginForm from "./LoginForm";
import MeetingPage from "./MeetingPage";
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {LoginForm, MeetingPage, NewMeetingForm, MeetingsList},

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
    }
  }
}


</script>

<style>

</style>
