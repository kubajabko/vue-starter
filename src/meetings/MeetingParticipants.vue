<template>
    
</template>

<script>
    export default {
        props: ['username'],
        data() {
            return {
                participants: {},
            };
        },
        methods: {
            addNewParticipant() {
                this.$emit('added', this.participants);
                this.participants = {};
            },
            deleteParticipant() {
                this.participants = {};
            }
        }
    }
</script>


<style scoped>

</style>