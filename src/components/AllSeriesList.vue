<template lang="html">
    <div>
        <h2>Select A Series:</h2>
        <span id="reminder">(Series in production are not included)</span>
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



.reminder {
    font-style: italic;
}

</style>