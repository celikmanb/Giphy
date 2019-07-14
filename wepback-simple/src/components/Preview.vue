<template>
    <div>
        <ul>
            <li v-for="(gif, index) in gifs">
                <div @mouseover="showClipboard(index)"
                     @mouseleave="closeClipboard"
                >
                    <VueLoadImage class="vue_load">
                        <img class="loaded_image" slot="image" :src="gif.images.fixed_height.url">
                        <img class="pre_image" slot="preloader" src="../assets/image-loader.gif"/>
                    </VueLoadImage>

                    <div v-if="visible && selectedIndex === index" class="shared">
                        <button v-clipboard="gif.images.fixed_height.url" class="copied">Copy</button>
                        <whats-app :url="gif.images.fixed_height.url"
                                   title="Gipyh image"
                                   scale="2"
                        >
                        </whats-app>
                    </div>

                </div>


            </li>
        </ul>
    </div>
</template>

<script>
    import { WhatsApp } from 'vue-socialmedia-share';
    import VueLoadImage from 'vue-load-image'

    export default {
        name: "Preview",
        props: [ 'gifs' ],
        components: {
            WhatsApp,
            VueLoadImage
        },
        data () {
            return {
                visible: false,
                selectedIndex: null,
                hover: false
            }
        },
        methods: {
            showClipboard(index) {
                this.selectedIndex = index;
                this.visible = true;
            },
            closeClipboard() {
                this.selectedIndex = null;
                this.visible = false;
            }
        }
    }
</script>

<style lang="scss" scoped>
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
    .shared:hover > .loaded_image {
        opacity: 0.4;
    }
    .copied {
        width: 80px;
        height: 30px;
        border-radius: 40px;
        color: white;
        background-color: #17a2b8;
        border: 1px solid transparent;
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

        /*&:hover:has(> img.hover) {
            opacity: 0.4;
        }*/

        /*&::after {
            img:hover {
                opacity: 0.4;
            }
        }*/

    }



</style>