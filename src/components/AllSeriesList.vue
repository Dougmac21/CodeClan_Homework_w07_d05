<template lang="html">
    <div>
        <ul>
            <all-series-list-item
            v-for="(series, index) in allSeries" :series="series" :key="index">
            </all-series-list-item>
        </ul>
        <hr>
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

.testing {
  color: red;
}

</style>