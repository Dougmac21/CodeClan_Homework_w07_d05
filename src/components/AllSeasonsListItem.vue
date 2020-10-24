<template>
  <div>
      <ul>
            <li v-on:click='handleClick'>
            <span>{{ season.title }}: </span>
            <span> | {{ season.numberOfEpisodes }} episodes</span>
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
        handleClick() {
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

            <!-- v-if="season.series.title === series.title" -->
