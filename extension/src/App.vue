<template>
    <div id="app">
        <div id="bcg" v-bind:style="{ 'background-image': 'url(' + imageUrl + ')' }">
            <TabHomePage />
            <div id="credits">{{ credits }}</div>
        </div>
    </div>
</template>

<script>
import TabHomePage from './components/TabHomePage.vue';
import PHOTO_ENDPOINT from './data/constants';
export default {
    name: 'App',
    data() {
        return {
            imageUrl: '',
            credits: '',
        };
    },
    mounted: function() {
        this.setImage();
    },
    methods: {
        setImage() {
            const fetchBackground = async () => {
                const response = await fetch(PHOTO_ENDPOINT);
                const json = await response.json();
                if (json) {
                    this.imageUrl = json.urls.regular;
                    this.credits = 'credits:' + json.user.name;
                } else {
                    this.imageUrl = `https://source.unsplash.com/random/landscape`;
                    this.credits = 'credits: http://www.unsplash.com';
                }
            };
            fetchBackground();
        },
    },
    components: {
        TabHomePage,
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: -22px;
    height: 100vh;
}
#bcg {
    width: 100%;
    opacity: 0.9;
    z-index: -2;
    height: 100vh;
}
#credits {
    text-align: right;
    z-index: 2;
    color: white;
    position: fixed;
    bottom: 13px;
    right: 13px;
}
</style>
