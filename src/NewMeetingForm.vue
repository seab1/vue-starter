<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Add new meeting</h3>
            <label>Name</label>
            <input type="text" v-model="newMeeting.name">
            <label>Description</label>
            <textarea v-model="newMeeting.description"></textarea>
			<h5 v-if="!newMeeting.name" style="color:red;">Please insert meeting name!</h5>
            <button v-else>Add</button>
        </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {}
      };
  },
  methods: {
      addNewMeeting() {
        this.$emit('added', this.newMeeting);
        this.newMeeting = {};
    }
  }
}
</script>