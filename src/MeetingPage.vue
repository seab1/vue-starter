<template>
    <div>
       <h2>Meetings</h2>
	   <button v-if="!seizeForm" @click="addingMeetingPossible()">Add new meeting</button>
       <new-meeting-form v-else @added="addNewMeeting($event)"></new-meeting-form>
	   <h4 v-if="meetings.length == 0" style="padding-top: 40px">No meetings yet!</h4>
	   <h4 v-else style="padding-top: 40px">Planned meetings ({{meetings.length}})</h4>
       <meetings-list :meetings="meetings" :user="user"></meetings-list>
    </div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  components: {NewMeetingForm, MeetingsList},
  props: ['seizeForm', 'user'],
  data() {
      return {
		  meetings: []
	  };
  },
  methods: {
	  addNewMeeting(meeting)
	  {
		  if(this.meetings.length > 0)
		  {
			  for(var i = 0; i < this.meetings.length; i++)
			  {
				  if(this.meetings[i].name == meeting.name)
				  {
					  alert("Meeting with that name already exists!");
					  return null;
				  }
			  }
		  }
		  this.meetings.push(meeting);
		  this.seizeForm = false;
	  },

	  addingMeetingPossible() {this.seizeForm = true;}
  }
}
</script>