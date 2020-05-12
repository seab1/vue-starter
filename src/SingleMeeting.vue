<template>
    <table style="border:0px; padding:0; margin:0; border-collapse:collapse; height:70px; word-break:break-all">
        <tbody>
				<td width="300px"> {{meetingName}} </td>
                <td width="400px"> {{meetingDescription}} </td>
				<td width="400px">
 					<li v-for="participant in participants" :key="participant.id">{{ participant }}</li>
				</td>
				<span v-if="participants.length < 1">
				<td width="0px" style="text-align:center"><button @click="deleteMe()">Delete</button></td>
				<td width="0px" style="text-align:center; padding:0"><button @click="assignMe()">Sign in</button></td>
				</span>
        </tbody>
    </table>
</template>

<script>
export default {
	props: ['meetingName', 'meetingDescription', 'userWannabe'],

	data() {
		return {
			participants: []
		};
	},
	  
	methods:
	{
		deleteMe()
		{
			this.$emit('deleteEmptyMeeting', this.meetingName);
		},

		assignMe()
		{
			if(!this.participants.includes(this.userWannabe)) this.participants.push(this.userWannabe);
		}
	}
}
</script>
