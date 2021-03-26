<template>
    <div class="d-flex justify-content-center">
        <form @submit.prevent="handleForm">
            <input type="text" placeholder="Description..." v-model="state.desc">
            <input type="number" placeholder="Value..." v-model="state.value">
            <input type="date" v-model="state.date">
            <input type="submit" placeholder="SUBMIT" class="bg-warning inline-block" id="submit">
        </form>
    </div>
</template>

<script>
import { reactive } from 'vue';

export default {
    name: 'Form',
    setup(props, {emit}) {
        const state = reactive({
            desc: null,
            value: null,
            date: null
        });

        function handleForm() {
            emit('data-income', {
                desc: state.desc,
                value: parseInt(state.value),
                date: state.date
            });

            reset();
        }

        function reset()
        {
            state.desc = null;
            state.value = null;
            state.date = null;
        }

        return {
            state, handleForm, reset
        }
    }
}
</script>

<style>
input {
    border: none;
}
form {
    margin-top: 20px;
    background: #fff;
    height: 60px;
    padding: 0px 0px 0px 20px;
    border-top-left-radius: 30px;
    border-bottom-left-radius: 30px;
    border-top-right-radius: 30px;
    border-bottom-right-radius: 30px;
}
#submit {
    height: 100%;
    width: 120px;
    border-top-right-radius: 30px;
    border-bottom-right-radius: 30px;
}
input:focus {
    outline: none !important;
}
input {
    color: #000;
}
</style>