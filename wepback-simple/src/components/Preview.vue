<template>
    <div>
        <ul>
            <li v-for="(gif, index) in gifs">
                <Card :gif="gif" :index="index" ref="clearList">

                </Card>

                <!--<div @mouseover="showClipboard(index)"
                     @mouseleave="closeClipboard"
                >
                    <VueLoadImage class="vue_load" @onLoad="handleHover(index)">
                        <img class="loaded_image" slot="image"
                             :src="gif.images.fixed_height.url"
                             :class="{'hover_image':visible && selectedIndex === index}">
                        <img class="pre_image" slot="preloader" src="../assets/image-loader.gif"/>
                    </VueLoadImage>

                    <div v-if="visible && selectedIndex === index && loadedImage.includes(index)" class="shared">
                        <button v-clipboard="gif.images.fixed_height.url" class="copied">Copy</button>
                        <whats-app :url="gif.images.fixed_height.url"
                                   title="Gipyh image"
                                   scale="2"
                        >
                        </whats-app>
                    </div>
                </div>-->


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