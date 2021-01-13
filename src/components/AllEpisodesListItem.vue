<template>
    <div>
        <li
        
        v-on:click='handleEpisodeClick'
        >
        <span id="episode-number">Episode {{ episode.episodeNumber }}</span>
        </li>
        <li

        v-on:click='handleEpisodeClick'
        >
        <span id="episode-title"> - {{ episode.title }}</span>
        </li>
        <li>
        <br>
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

<style lang="css" scoped>



li {

    cursor: pointer;
}
.testing {
  color: red;
}
</style>