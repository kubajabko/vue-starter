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
                    <li v-for="item in meeting.contestants" :key="item.id">{{ item }}</li>
                </ol>
            </td>
            <td>
                <div v-if="meeting.contestants.length = 0">
                    <button @click="deleteNewContestant(meeting.id)">Wypisz się</button>
                </div>
                <div v-else>
                    <button @click="addNewContestant(meeting.id)">Zapisz się</button>
                </div>
            </td>
        </tr>
        </tbody>
    </table>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    export default {
        props: ['meetings', 'username'],
        components: {NewMeetingForm},
        methods: {
            addNewContestant(username, id) {
                NewMeetingForm.getElementById(id).contestants.push(username);
            },
            deleteNewContestant(username, id) {
                NewMeetingForm.getElementById(id).contestants.delete(username)
            }
        }
    }

</script>

<style scoped>

</style>