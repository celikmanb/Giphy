<template>
    <div class="search">
        <input type="text" v-model="query" @keypress.enter="handleSearch"/>
        <button @click="handleSearch">Search</button>
    </div>
</template>

<script>
    export default {
        name: "Search",
        data() {
            return {
                query: ''
            }
        },
        methods: {
            handleSearch() {
                this.$emit('SearchRequested', this.query);
            }
        }
    }
</script>

<style scoped>
    .search {
        display: flex;
        justify-content: center;
    }
    input {
        padding: 10px 20px;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 900px;
    }
    button {
        padding: 5px 15px;
        border: 1px solid #ccc;
        background-color: #4183c4;
        color: #fff;
        font-size: 16px;
        border-radius: 5px;
    }
</style>