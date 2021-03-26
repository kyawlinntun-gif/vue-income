<template>
    <div class="vue-income">
        <Header :totalIncome="state.totalIncome"></Header>
        <Form v-on:dataIncome="handleIncome"></Form>
        <income-list :state="state.income"></income-list>
    </div>
</template>

<script>
import Header from './components/Header';
import Form from './components/Form';
import IncomeList from './components/IncomeList.vue';
import { reactive, computed } from 'vue';

export default {
    name: 'App',
    setup()
    {
        const state = reactive({
            income: [],
            totalIncome: computed(() => {
                let temp = 0;
                if(state.income.length > 0) {
                    for(let i = 0; i < state.income.length; i++)
                    {
                        temp += state.income[i].value;
                    }
                }
                return temp;
            })
        });

        function handleIncome(data) {
            let d = data.date.split("-");
            let newD = new Date(d[0], d[1], d[2]);

            let fullDate = newD;
            let day = fullDate.getDate();
            let month = fullDate.getMonth();
            let year = fullDate.getFullYear();

            let formattedDate = day + '/' + month + '/' + year;

            state.income = [
                ...state.income,
                {
                    id: Date.now(),
                    desc: data.desc,
                    value: data.value,
                    date: formattedDate
                }
            ]
        }

        return {
            Header, state, Form, handleIncome, IncomeList
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