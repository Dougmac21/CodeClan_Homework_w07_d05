<template>
    <div>
        <ul>
            <li
            v-if="series.productionStartYear != null"
            v-on:click='handleClick'
            >
            <span>    {{ series.title }}: </span>
            <span>( {{ series.productionStartYear }} - {{ series.productionEndYear }} )</span>
            <span>
                <button v-on:click=>Select</button>
            </span>
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
        handleClick() {
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
</style>