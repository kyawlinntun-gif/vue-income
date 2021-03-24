<template>
    <div>
        <header>
            <h1>Income Tracker</h1>
            <span class="badge badge-pill bg-warning">&#163; {{ totalIncome }}</span>
        </header>
        <div class="yellow"></div>
    </div>
</template>

<script>
export default {
    name: 'Header',
    props: {
        totalIncome: {
            type: Number,
            required: true
        }
    }
}
</script>

<style scoped>
header {
    height: 100px;
    background: midnightblue;
    display: flex;
    justify-content: space-between;
    padding: 0 40px 0 40px;
    align-items: center;
}
header > span {
    font-size: 30px;
}
.yellow {
    height: 10px;
    background: yellow;
}
</style>