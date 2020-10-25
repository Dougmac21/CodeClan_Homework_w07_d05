<template>
    <article class="all-series-list-item">
            <li
            v-if="series.productionStartYear !== null"
            v-on:click='handleSeriesClick'
            >
            <span id="series-title">    {{ series.title }}</span>
            <hr>
            <span id="series-years">( {{ series.productionStartYear }} - {{ series.productionEndYear }} )</span>
            </li>
    </article>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-series-list-item',
    props: ['series'],
    methods: {
        handleSeriesClick() {
            eventBus.$emit('series-selected', this.series)
        }
    }
}
</script>

<style lang="css" scoped>

.all-series-list-item {
    display: grid;
}




li {
    display: flex;
    cursor: pointer;
}



</style>