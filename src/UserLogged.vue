<template>
    <div>
        <h3>Witaj {{username}}!
            <button @click="logout()">{{buttonLabelToDisplay}}</button>
        </h3>
    </div>
</template>

<script>
    export default {
        props: ['username'],
        methods: {
            logout() {
                this.$emit('logout');
            },
        }, computed: {
            buttonLabelToDisplay() {
                return this.buttonLabel || 'Wyloguj się';
            }
        }
    }
</script>

<style scoped>

</style>