<template>
    <table v-if="meetings.length > 0">
        <thead>
        <tr>
            <th>Nazwa spotkania</th>
            <th>Opis</th>
            <th>Uczestnicy</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="meeting in meetings" :key="meeting.name">
            <td>{{ meeting.name }}</td>
            <td>{{ meeting.description }}</td>
            <td>
                <ol>
                    <li v-for="participant in meeting.participants" :key="participant.id">{{ participant }}</li>
                </ol>
            </td>
            <td>
                    <button @click="deleteParticipant(meeting.name)" v-if="participantAdded(meeting.participants)">Wypisz się</button>
                    <button @click="addNewParticipant(meeting.name)" v-if="!participantAdded(meeting.participants)">Zapisz się</button>
                    <button @click="deleteMeeting(meeting.name)" v-if="meeting.participants.length ===0">Usuń puste spotkanie</button>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'username'],
        methods: {
            addNewParticipant(meetingName) {
                this.$emit('addparticipant', meetingName);
            },
            deleteParticipant(meetingName) {
                this.$emit('deleteparticipant', meetingName);
            },
            deleteMeeting(meetingName) {
                this.$emit('deletemeeting', meetingName)
            },
            participantAdded(participants) {
                if (participants == null || participants.length === 0) return false;
                return participants.includes(this.username);
            }
        }
    }

</script>

<style scoped>

</style>