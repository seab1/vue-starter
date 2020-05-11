<template>
    <table v-if="meetings.length > 0">
        <thead>
            <tr>
                <th>Meeting name</th>
                <th>Description</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: ['meetings']
}
</script>