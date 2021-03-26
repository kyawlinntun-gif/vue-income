<template>
    <div id="income-item" v-for="item in income" :key="item.id">
        <span class="text-danger" style="margin-right: 20px; cursor: pointer;">X</span>
        <p class="text-dark d-inline-block p-0 m-0">{{ item.desc }}</p>
        <span class="text-dark float-end" style="margin-left: 40px;">{{ item.date }}</span>
        <span class="text-dark float-end">&#163; {{ item.value }}</span>
    </div>
</template>

<script>
export default {
    name: 'IncomeItem',
    props: {
        income: {
            type: Object
        }
    }
}
</script>

<style scoped>
#income-item {
    background: #fff;
    height: 70px;
    border-radius: 10px;
    margin-top: 20px;
    line-height: 70px;
    padding: 0 25px 0 25px;
}
</style>