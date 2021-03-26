<template>
    <div id="income-list">
        <income-item :income="state"></income-item>
    </div>
</template>

<script>
import IncomeItem from './IncomeItem.vue';

export default {
    name:"IncomeList",
    props: {
        state: Object
    },
    setup()
    {
        return {
            IncomeItem
        }
    }
}
</script>
<style scoped>
#income-list {
    margin: 0 auto;
    width: 800px;
}
</style>