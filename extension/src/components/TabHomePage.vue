<template>
    <div>
        <h1>🎃 Hacktoberfest 2020 New Tab Page 🎃</h1>

        <MostViewed />
    </div>
</template>

<script>
import MostViewed from './most-viewed/MostViewed.vue';
export default {
    name: 'TabHomePage',
    components: { MostViewed },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
$link-color: #42b983;

h3 {
    margin: 40px 0 0;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: $link-color;
}
</style>
