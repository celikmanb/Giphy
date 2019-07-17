<template>
    <div>
        <ul>
            <li v-for="(gif, index) in gifs">
                <Card :gif="gif" :index="index" ref="clearList">

                </Card>
            </li>
        </ul>
    </div>
</template>

<script>
    import Card from './Card';

    export default {
        name: "Preview",
        props: [ 'gifs' ],
        components: {
            Card,
        },
        data () {
            return {
                loadedImage:[]
            }
        },
        methods: {
            clearLoaded(value) {
                if (value) {
                    this.$refs.clearList.clearData();
                }
            }
        },

    }
</script>

<style lang="scss">
    li {
        list-style:none;
        float: left;
        margin: 20px;
        position: relative;
    }
    .vue_load {
        position: relative;
    }
    .vue_load:hover > .loaded_image {
        opacity: 0.4;
    }
    .hover_image {
        opacity: 0.4;
    }
    .copied {
        width: 80px;
        height: 30px;
        border-radius: 40px;
        color: white;
        background-color: #17a2b8;
        border: 1px solid transparent;
        margin-right: 12px;
    }
    img {
        display: flex;
        opacity: 1;
    }
    .shared {
        display: inline-flex;
        position: absolute;
        align-items: center;
        top: 40%;
        right: 30%;

    }



</style>