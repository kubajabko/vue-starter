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
                    <li v-for="participant in participants" :key="participant.id">{{ participant }}</li>
                </ol>
            </td>
            <td>
                <div v-if="participants.length > 0">
                    <button @click="deleteParticipant">Wypisz się</button>
                </div>
                <div v-else>
                    <button @click="addNewParticipant">Zapisz się</button>
                </div>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    export default {
        props: ['meetings', 'username', 'participants'],
        methods: {
            addNewParticipant(username) {
                this.participants.push(username);
            },
            deleteParticipant(username) {
                this.participants.delete(username)
            }
        }
    }

</script>

<style scoped>

</style>