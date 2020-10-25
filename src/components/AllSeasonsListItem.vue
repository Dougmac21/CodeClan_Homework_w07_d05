<template>
    <article>
        <li
        
        v-on:click='handleSeasonClick'
        >
        <span id="season-title">{{ season.title }}</span>
        </li>
        <li
        
        v-on:click='handleSeasonClick'
        >
        <span id="season-num-eps">{{ season.numberOfEpisodes }} episodes</span>
        </li>
        <li
        
        >
        <br>
        </li>
    </article>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-seasons-list-item',
    props: ['season'],
    methods: {
        handleSeasonClick() {
            eventBus.$emit('season-selected', this.season)
            eventBus.$emit('episode-selected', null)
        }
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

li {
    display: flex;
    cursor: pointer;
}

.testing {
  color: red;
}

</style>