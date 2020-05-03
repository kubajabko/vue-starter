<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <meetings-list :meetings="meetings" :username="username" :participants="participants"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";
    import MeetingParticipants from "./MeetingParticipants";

    export default {
        props: ['username', 'participants'],
        components: {NewMeetingForm, MeetingsList, MeetingParticipants},
        data() {
            return {
                meetings: []
            };
        },
        methods: {
            addNewMeeting(meeting) {
                this.meetings.push(meeting);
            }
        }
    }
</script>

<style scoped>

</style>