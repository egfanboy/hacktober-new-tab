<template>
    <div id="example-2">
        <button v-on:click="greet">Hacktoberfest</button>
    </div>
</template>
<script>
export default {
    name: 'Button',
    data: function() {
        return {
            myModel: false,
        };
    },
    methods: {
        greet: function() {
            window.open('https://hacktoberfest.digitalocean.com/', '_blank');
        },
    },
};
</script>
