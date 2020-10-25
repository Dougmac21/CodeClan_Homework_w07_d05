<template lang="html">
  <main>
    <h1
    v-on:click='handleTitleClick'
    >Star TrekkR</h1>
    <article class ="main-container">
      <all-series-list :allSeries='allSeries'></all-series-list>
      <series-details :series='selectedSeries' :allSeasons='allSeasons'></series-details>
      <!-- <all-seasons-list :allSeasons='allSeasons.seasons'></all-seasons-list> -->
      <season-details :season='selectedSeason' :allEpisodes='allEpisodes'></season-details>
      <!-- <all-episodes-list :allEpisodes='allEpisodes.episodes'></all-episodes-list> -->
      <episode-details :episode='selectedEpisode'></episode-details>
    </article>
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
    handleTitleClick() {
      alert("Don't click there...")
    },

    getSeriesData: function() {
      fetch("http://stapi.co/api/v1/rest/series/search")
      .then(res => res.json())
      .then(all_series => this.allSeries = all_series.series)
      .then(() => this.sortSeries("productionStartYear"))
    },

    sortSeries: function(seriesProperty) {
      this.allSeries.sort((seriesA, seriesB) => {
        return seriesA[seriesProperty] < seriesB[seriesProperty] ? -1 : 1;
      });
    },

    getSeasonData: function() {
      fetch("http://stapi.co/api/v1/rest/season/search")
      .then(res => res.json())
      .then(all_seasons => this.allSeasons = all_seasons.seasons)
      .then(() => this.sortSeasons("seasonNumber"))
    },

    sortSeasons: function(seasonProperty) {
      this.allSeasons.sort((seasonA, seasonB) => {
        return seasonA[seasonProperty] < seasonB[seasonProperty] ? -1 : 1;
      });
    },

    getEpisodeData: function() {
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=0&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_0 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_0.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=1&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_1 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_1.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=2&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_2 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_2.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=3&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_3 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_3.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=4&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_4 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_4.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=5&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_5 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_5.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=6&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_6 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_6.episodes))
      
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=7&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes_7 => this.allEpisodes.push.apply(this.allEpisodes, all_episodes_7.episodes))

      .then(() => this.sortEpisodes("episodeNumber"))
    },

    sortEpisodes: function(episodeProperty) {
      this.allEpisodes.sort((episodeA, episodeB) => {
        return episodeA[episodeProperty] < episodeB[episodeProperty] ? -1 : 1;
      });
    },

    // getEveryEpisodeData: function() {
    //   const promises = [1, 2, 3, 4, 5, 6, 7].map(pageNumber => {
    //     return fetch(
    //       `http://stapi.co/api/v1/rest/episode/search?pageNumber=${pageNumber}&pageSize=100&numberOfElements=100`
    //       )
    //       .then(res => res.json())
    //   });
    
    //   Promise.all(promises)
    //     .then(everyEpisodeData => this.allEpisodes = everyEpisodeData.episodes)
    //       .then(() => this.sortEpisodes("episodeNumber"))
    // },
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
    // this.getEveryEpisodeData();

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
h1 {
  color: wheat;
  background-color: rgb(43, 43, 43);
  width: 100vw;
  height: 5vh;
  text-align: left;
  font-family: 'Times New Roman', Times, serif;
  text-decoration: underline;
}

.main-container {
  color: wheat;
  background-color: rgb(43, 43, 43);
  width: 100vw;
  height: 90vh;
  margin: 0 auto;
  font-family: 'Times New Roman', Times, serif;
  display: grid;
  grid-template-columns: 25vw 25vw 25vw 25vw;
}

ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}


</style>