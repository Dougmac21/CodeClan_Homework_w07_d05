<template lang="html">
    <div>
        <h2>Select A Series:</h2>
        <ul>
            <all-series-list-item
            v-for="(series, index) in allSeries" :series="series" :key="index">
            </all-series-list-item>
        </ul>
    </div>
</template>

<script>
import AllSeriesListItem from './AllSeriesListItem.vue'

export default {
    name: 'all-series-list',
    props: ['allSeries'],
    components: {
        'all-series-list-item': AllSeriesListItem
    }
}
</script>

<style lang="css" scoped>

ul {
    list-style: none;
    padding-left: 0;
    height: 90vh;
    overflow-y: auto;
}

.reminder {
    font-style: italic;
}

</style>