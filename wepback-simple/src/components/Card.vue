<template>
    <div @mouseover="showClipboard(index)"
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
    </div>
</template>

<script>
    import { WhatsApp } from 'vue-socialmedia-share';
    import VueLoadImage from 'vue-load-image'

    export default {
        name: "Card",
        props: {
            gif: {
                type: Object,
                required: true
            },
            index: {
                type: Number,
                required: true
            }
        },
        components: {
            WhatsApp,
            VueLoadImage
        },
        data() {
            return {
                visible: false,
                selectedIndex: null,
                loadedImage:[]
            }
        },
        watch: {
            clearList(value) {
                if (value) {
                    this.loadedImage = [];
                }
            }
        },
        methods: {
            handleHover(data) {
                this.loadedImage.push(data);
            },
            showClipboard(index) {
                this.selectedIndex = index;
                this.visible = true;
            },
            closeClipboard() {
                this.selectedIndex = null;
                this.visible = false;
            },
            clearData() {
                this.loadedImage = [];
            }
        }
    }
</script>

<style scoped>

</style>