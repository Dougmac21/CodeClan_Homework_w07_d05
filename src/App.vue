<template lang="html">
  <main>
    <h1>Star TrekkR</h1>
    <div class ="main-container">
      <all-series-list :allSeries='allSeries.series'></all-series-list>
      <hr>
      <series-details :series='selectedSeries'></series-details>
      <hr>
    </div>
  </main>
</template>

<script>
import AllSeriesList from './components/AllSeriesList';
import SeriesDetails from './components/SeriesDetails';
import AllSeasonsList from './components/AllSeasonsList';
import SeasonDetails from './components/SeasonDetails';
import AllEpisodesList from './components/AllEpisodesList';
import EpisodeDetails from './components/EpisodeDetails';

import { eventBus } from '@/main.js';

export default {
  name: 'app',
  data() {
    return {
      allSeries: [],
      selectedSeries: null,
      allSeasons: [],
      selectedSeason: null,
      allEpisodes: [],
      selectedEpisode: null
    }
  },
  methods: {

  },
  components: {
    "all-series-list": AllSeriesList,
    "series-details": SeriesDetails,
    "episode-details": EpisodeDetails
  },
  mounted() {
    fetch("http://stapi.co/api/v1/rest/series/search")
    .then(res => res.json())
    .then(all_series => this.allSeries = all_series)

    // fetch("http://stapi.co/api/v1/rest/season/search")
    // .then(res => res.json())
    // .then(all_seasons => this.allSeasons = all_seasons)

    // fetch("http://stapi.co/api/v1/rest/episode/search")
    // .then(res => res.json())
    // .then(all_episodes => this.allEpisodes = all_episodes)


    eventBus.$on('series-selected', (series) => {
      this.selectedSeries = series;
    })
  }
}
</script>

<style lang="css" scoped>

</style>