<template>
  <div>
    <h1>AllSeriesListItem</h1>

    <li v-on:click='handleClick'> {{ series.name }}</li>

  </div>
</template>

<script>
import { eventBus } from '@/main.js';

export default {
    name: 'all-series-list-item',
    props: ['series'],
    methods: {

    }

}
</script>

<style lang="css" scoped>

</style>