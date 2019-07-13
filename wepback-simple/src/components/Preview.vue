<template>
    <div>
        <ul>
            <li v-for="(gif, index) in gifs">
                <img :src="gif.images.fixed_height.url">
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "Preview",
        props: [ 'gifs' ],
        data () {
            return {

            }
        }
    }
</script>

<style scoped>
    li {
        list-style:none;
        float: left;
        margin: 20px;
    }
</style>