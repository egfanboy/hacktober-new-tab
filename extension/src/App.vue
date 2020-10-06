<template>
    <div id="app">
        <TabHomePage />
    </div>
</template>

<script>
import TabHomePage from './components/TabHomePage.vue';

export default {
    name: 'App',
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
    margin-top: 60px;
}
</style>
