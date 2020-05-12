<template>
<div>
    <table v-if="meetings.length > 0" style="border:0px; padding:0; margin:0; border-collapse:collapse; height:70px">
        <thead>
                <th width="185px">Meeting name</th>
                <th width="240px">Description</th>
				<th width="400px">Participants</th>
        </thead>
    </table>
	
	<table>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <single-meeting :meetingName=meeting.name :meetingDescription=meeting.description
				@deleteEmptyMeeting="deleteMeeting($event)"></single-meeting>
            </tr>
        </tbody>
    </table>
</div>
</template>

<script>
import SingleMeeting from "./SingleMeeting";

export default {
	components: {SingleMeeting},
	props: ['meetings'],
	methods:
	{
		deleteMeeting(nameToBeDeleted)
		{
		  if(this.meetings.length > 0)
		  {
			  for(var i = 0; i < this.meetings.length; i++)
			  {
				  if(this.meetings[i].name == nameToBeDeleted)
				  {
					  this.meetings.splice(i, 1);
				  }
			  }
		  }
	  }
	}
}
</script>