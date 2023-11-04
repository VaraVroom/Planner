<template>
    <nav class="filter-app">
    <button @click="updateFilter('all')" :class="{active:current === 'all'}">All Projects</button>
    <button @click="updateFilter('completed')" :class="{active:current === 'completed'}">Completed Projects</button>
    <button @click="updateFilter('ongoing')" :class="{active:current === 'ongoing'}">Ongoing Projects</button>
    </nav>
</template>

<script>
export default{
    props:['current'],
    methods:{
        updateFilter(by){
            this.$emit('filterChange',by);
        }
    }
};
</script>

<style>
    .filter-app{
        display: flex;
        flex-direction: row;
        justify-content: center;
    }
    .filter-app button {
        background: none;
        border: none;
        outline: none;
        color: black;
        font-size: 15px;
        text-transform: uppercase;
        margin-right: 10px;
        letter-spacing: 1px;
        font-weight: bold;
        cursor: pointer;
    }
    .filter-app button.active {
        color: #c3a709;
    }
</style>