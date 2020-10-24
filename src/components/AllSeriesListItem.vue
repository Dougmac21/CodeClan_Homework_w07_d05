<template>
  <div>
      <ul>
          <li v-on:click='handleClick'> {{ series.title }}</li>
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