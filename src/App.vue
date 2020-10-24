<template lang="html">
  <main>
    <h1>Star TrekkR</h1>
    <div class ="main-container">
      <series-list :allSeries='allSeries'></series-list>
      <hr>
      <series-details :series='selectedSeries'></series-details>
      <hr>
    </div>
  </main>
</template>

<script>
import AllSeriesList from './components/AllSeriesList';
import SeriesDetails from './components/SeriesDetails';

import { eventBus } from '@/main.js'

export default {
  name: 'app',
  data() {
    return {
      allSeries: [],
      selectedSeries: null,
      allSeasons: [],
      selectedSeason: null
    }
  },
  methods: {

  },
  components: {
    "all-series-list": AllSeriesList,
    "series-details": SeriesDetails,
  },
  mounted() {
    fetch("http://stapi.co/api/v1/rest/season/search")
    .then(res => res.json())
    .then(all_seasons => this.allSeasons = all_seasons)

  }
}
</script>

<style>

</style>