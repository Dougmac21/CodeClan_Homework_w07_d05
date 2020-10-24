<template>
  <div>
      <ul>
          <li v-on:click='handleClick'>Season: {{ season.seasonNumber }}</li>
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