<template>
    <div class="vue-income">
        <Header :totalIncome="state.totalIncome"></Header>
        <Form v-on:dataIncome="handleIncome"></Form>
    </div>
</template>

<script>
import Header from './components/Header';
import Form from './components/Form';
import { reactive, computed } from 'vue';

export default {
    name: 'App',
    setup()
    {
        const state = reactive({
            income: [],
            totalIncome: computed(() => {
                let temp = 0;
                for(var i = 0; i < state.income.length; i++)
                {
                    temp += parseInt(state.income[i].value);
                }
                return temp;
            })
        });

        function handleIncome(data) {
            state.income = [
                ...state.income,
                {
                    id: Date.now(),
                    desc: data.desc,
                    value: data.value,
                    date: data.date
                }
            ]
        }

        return {
            Header, state, Form, handleIncome
        }
    }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Times New Roman', Times, serif;
    font-size: 25px;
    color: #fff;
}
</style>