<template>
    <div>
        <ul>
            <li
            
            v-on:click='handleSeasonClick'
            >
            <span id="season-title">{{ season.title }}: </span>
            <span id="season-num-eps"> | {{ season.numberOfEpisodes }} episodes</span>
            </li>
        </ul>

    </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-seasons-list-item',
    props: ['season'],
    methods: {
        handleSeasonClick() {
            eventBus.$emit('season-selected', this.season)
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