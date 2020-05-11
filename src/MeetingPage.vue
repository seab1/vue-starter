<template>
    <div>
       <h2>Classes</h2>
	   <button v-if="!seizeForm" @click="addingMeetingPossible()">Add new meeting</button>
       <new-meeting-form v-else @added="addNewMeeting($event)"></new-meeting-form>
	   <h4 v-if="meetings.length == 0">No meetings yet!</h4>
	   <h4 v-else>Planned meetings ({{meetings.length}})</h4>
       <meetings-list :meetings="meetings"></meetings-list>
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {NewMeetingForm, MeetingsList},
  props: ['seizeForm'],
  data() {
      return {
		  meetings: []
	  };
  },
  methods: {
	  addNewMeeting(meeting) {this.meetings.push(meeting); this.seizeForm=false;},
	  addingMeetingPossible() {this.seizeForm=true;}
  }
}
</script>