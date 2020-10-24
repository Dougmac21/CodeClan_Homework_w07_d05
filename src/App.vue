<template lang="html">
  <main>
    <h1>Star TrekkR</h1>
    <div class ="main-container">
      <p class="testing">appmain seriesList</p>
      <all-series-list :allSeries='allSeries.series'></all-series-list>
      <br>
      <p class="testing">appmain seriesDetails</p>
      <series-details :series='selectedSeries', :allSeasons='allSeasons.seasons'></series-details>
      <hr>
      <p class="testing">appmain seasonsList</p>
      <all-seasons-list :allSeasons='allSeasons.seasons'></all-seasons-list>
      <br>
      <p class="testing">seasonDetails</p>
      <season-details :season='selectedSeason', :allEpisodes='allEpisodes.episodes'></season-details>
      <hr>
      <p class="testing">appmain allEpisodesList</p>
      <all-episodes-list :allEpisodes='allEpisodes.episodes'></all-episodes-list>
      <br>
      <p class="testing">appmain episodeDetails</p>
      <episode-details :episode='selectedEpisode'></episode-details>
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
    getSeriesData: function() {
      fetch("http://stapi.co/api/v1/rest/series/search")
      .then(res => res.json())
      .then(all_series => this.allSeries = all_series)
      .then(() => this.sortSeries("productionStartYear"))
    },

    sortSeries: function(seriesProperty) {
      this.allSeries.series.sort((seriesA, seriesB) => {
        return seriesA[seriesProperty] < seriesB[seriesProperty] ? -1 : 1;
      });
    },

    getSeasonData: function() {
    fetch("http://stapi.co/api/v1/rest/season/search")
    .then(res => res.json())
    .then(all_seasons => this.allSeasons = all_seasons)
    .then(() => this.sortSeasons("seasonNumber"))
    },

    sortSeasons: function(seasonNumber) {
      this.allSeasons.seasons.sort((seasonA, seasonB) => {
        return seasonA[seasonNumber] < seasonB[seasonNumber] ? -1 : 1;
      });
    },

    getEpisodeData: function() {
    fetch("http://stapi.co/api/v1/rest/episode/search")
    .then(res => res.json())
    .then(all_episodes => this.allEpisodes = all_episodes)
    .then(() => this.sortEpisodes("episodeNumber"))
    },

    sortEpisodes: function(episodeProperty) {
      this.allEpisodes.episodes.sort((episodeA, episodeB) => {
        return episodeA[episodeProperty] < episodeB[episodeProperty] ? -1 : 1;
      });
    }

  },

  components: {
    "all-series-list": AllSeriesList,
    "series-details": SeriesDetails,

    "all-seasons-list": AllSeasonsList,
    "season-details": SeasonDetails,

    "all-episodes-list": AllEpisodesList,
    "episode-details": EpisodeDetails
  },

  mounted() {
    this.getSeriesData();
    this.getSeasonData();
    this.getEpisodeData();

    // eventBus.$on('series-selected', series => (this.selectedSeries = series));

    eventBus.$on('series-selected', (series) => {
      this.selectedSeries = series;
    }),

    eventBus.$on('season-selected', (season) => {
      this.selectedSeason = season;
    }),

    eventBus.$on('episode-selected', (episode) => {
      this.selectedEpisode = episode;
    })
  }
}
</script>

<style lang="css" scoped>

.testing {
  color: red;
}

</style>