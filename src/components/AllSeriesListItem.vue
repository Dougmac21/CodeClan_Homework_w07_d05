<template>
    <div>
        <ul>
            <li
            v-if="series.productionStartYear !== null"
            v-on:click='handleSeriesClick'
            >
            <span id="series-title">    {{ series.title }}: </span>
            <span id="series-years">( {{ series.productionStartYear }} - {{ series.productionEndYear }} )</span>
            </li>
        </ul>
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
        }
    }
}
</script>

<style lang="css" scoped>
ul {
    list-style: none;
    cursor: pointer;
}

.testing {
  color: red;
}

</style>