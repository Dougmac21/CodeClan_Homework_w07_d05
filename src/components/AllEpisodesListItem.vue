<template>
  <div>
        <li
        
        v-on:click='handleEpisodeClick'
        >
        <span id="episode-number">{{ episode.episodeNumber }}</span>
        <span id="episode-title">: {{ episode.title }}</span>
        </li>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-episodes-list-item',
    props: ['episode'],
    methods: {
        handleEpisodeClick() {
            eventBus.$emit('episode-selected', this.episode)
        }
    }
}
</script>

<style land="css" scoped>
ul {
    list-style: none;
    cursor: pointer;
}
.testing {
  color: red;
}
</style>