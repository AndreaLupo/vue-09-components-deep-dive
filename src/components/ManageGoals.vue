<template>
    <div>
        <h1>Manage goals</h1>
        <input type="text" ref="goal">
        <button @click="setGoal">Set Goal</button>
        <teleport to="body">
            <error-alert v-if="isInputInvalid">
                <h2>Input is invalid!</h2>
                <p>Please insert some characters.</p>
                <button @click="confirmError">Ok</button>
            </error-alert>
        </teleport>
    </div>

</template>

<script>
import ErrorAlert from './ErrorAlert.vue';
export default {
    data () {
        return {
            isInputInvalid: false
        };
    },
    components: { ErrorAlert },
    methods: {
        setGoal() {
            const enteredValue = this.$refs.goal.value;
            if(enteredValue === '') {
                this.isInputInvalid = true;
            }
        },
        confirmError() {
            this.isInputInvalid = false;
        }
    }
}
</script>

<style>

</style>