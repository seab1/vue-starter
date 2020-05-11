<template>
  <div id>
    <h1>Welcome to the login system</h1>
    <div v-show="loggedIn">
      <h2> Bonjour, {{ loggedIn }} </h2>
      <button @click="logout()"> Log out </button>
      <meeting-page :seizeForm=forceClose></meeting-page>
    </div>

    <div v-show="!loggedIn">
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
      loggedIn: '',
      forceClose: false
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
      this.loggedIn = '';
    }
  }
}


</script>

<style>

</style>
