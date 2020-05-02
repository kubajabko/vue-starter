<template>
    <div>
        <h2>Zajęcia</h2>
        <new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
        <meetings-list :meetings="meetings" :username="username"></meetings-list>
    </div>
</template>

<script>
    import NewMeetingForm from "./NewMeetingForm";
    import MeetingsList from "./MeetingsList";

    export default {
        props: ['username'],
        components: {NewMeetingForm, MeetingsList},
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