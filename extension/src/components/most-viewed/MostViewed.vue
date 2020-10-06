<template>
    <div class="most-viewed">
        <h4>Most Visited</h4>
        <div class="most-viewed-container">
            <div
                v-on:click="openMostVisited(topSite)"
                class="most-viewed-item"
                v-for="topSite in topSites"
                :key="topSite.url"
            >
                <img :src="topSite.favicon" class="viewed-favicon" />
                <p class="viewed-text">
                    {{ topSite.title }}
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'MostViewed',
    data: function() {
        return { topSites: [] };
    },
    created: function() {
        chrome.topSites.get(topSites => {
            this.topSites = topSites.map(topSite => ({
                ...topSite,
                favicon: `chrome://favicon/${topSite.url}`,
            }));
        });
    },
    methods: {
        openMostVisited(site) {
            window.open(site.url, '_blank');
        },
    },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.most-viewed-container {
    display: flex;
    justify-content: center;
}
.most-viewed-item {
    margin: 1rem;
    justify-content: center;
    align-items: center;
    width: 100px;
    &:hover {
        cursor: pointer;
    }
}

.viewed-text {
    margin: 0;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.viewed-favicon {
    width: 20px;
    height: 20px;
    margin-right: 0.5rem;
}
</style>
