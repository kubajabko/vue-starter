<template>
    <div>
        <div v-show="authenticatedUsername">
            <h1>System zapisów na zajęcia</h1>
            <user-logged :username="this.authenticatedUsername" @logout="logMeOut($event)"></user-logged>
            <meeting-page :username="this.authenticatedUsername"></meeting-page>
        </div>
        <div v-if="authenticatedUsername === ''">
            <h1>Witaj w systemie zapisów na zajęcia</h1>
            <login-form @login="logMeIn($event)"></login-form>
        </div>
    </div>
</template>

<script>
    import "milligram";
    import LoginForm from "./LoginForm";
    import UserLogged from "./UserLogged";
    import MeetingPage from "./meetings/MeetingPage";

    export default {
        components: {UserLogged, LoginForm, MeetingPage},
        data() {
            return {
                authenticatedUsername: ''
            };
        },
        methods: {
            logMeIn(username) {
                this.authenticatedUsername = username;
            },
            logMeOut() {
                this.authenticatedUsername = '';
            }
        }
    }
</script>

<style>
</style>
