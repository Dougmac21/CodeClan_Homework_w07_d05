<template>
    <div class="all-series-list-item">
            <li
            v-if="series.productionStartYear !== null"
            v-on:click='handleSeriesClick'
            >
            <span id="series-title">    {{ series.title }}</span>
            </li>
            <li
            v-if="series.productionStartYear !== null"
            v-on:click='handleSeriesClick'
            >
            <span id="series-years">( {{ series.productionStartYear }} - {{ series.productionEndYear }} )</span>
            </li>
    </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-series-list-item',
    props: ['series'],
    methods: {
        handleSeriesClick() {
            eventBus.$emit('series-selected', this.series)
            eventBus.$emit('season-selected', null)
            eventBus.$emit('episode-selected', null)
        }
    }
}
</script>

<style lang="css" scoped>

.all-series-list-item {
    display: grid;
    grid-template-rows: 25 25 25 25;
}




li {
    display: flex;
    cursor: pointer;
}



</style>