<template lang="html">
  <main>
    <h1>Star TrekkR</h1>
    <div class ="main-container">
      <all-series-list :allSeries='allSeries'></all-series-list>
      <br>
      <series-details :series='selectedSeries' :allSeasons='allSeasons'></series-details>
      <hr>
      <!-- <all-seasons-list :allSeasons='allSeasons.seasons'></all-seasons-list> -->
      <br>
      <season-details :season='selectedSeason' :allEpisodes='allEpisodes'></season-details>
      <hr>
      <!-- <all-episodes-list :allEpisodes='allEpisodes.episodes'></all-episodes-list> -->
      <br>
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
      .then(all_series => this.allSeries = all_series.series)
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
      .then(all_seasons => this.allSeasons = all_seasons.seasons)
      .then(() => this.sortSeasons("seasonNumber"))
    },

    sortSeasons: function(seasonNumber) {
      this.allSeasons.seasons.sort((seasonA, seasonB) => {
        return seasonA[seasonNumber] < seasonB[seasonNumber] ? -1 : 1;
      });
    },

    getEpisodeData: function() {
      fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=0&pageSize=100&numberOfElements=100")
      .then(res => res.json())
      .then(all_episodes => this.allEpisodes = all_episodes.episodes)
      .then(() => this.sortEpisodes("episodeNumber"))
    },

    sortEpisodes: function(episodeProperty) {
      this.allEpisodes.episodes.sort((episodeA, episodeB) => {
        return episodeA[episodeProperty] < episodeB[episodeProperty] ? -1 : 1;
      });
    },

    // getEveryEpisodeData: function() {
    //   const promises = [1, 2, 3, 4, 5, 6, 7].map(pageNumber => {
    //     return fetch(
    //       `http://stapi.co/api/v1/rest/episode/search?pageNumber=${pageNumber}&pageSize=100&numberOfElements=100`
    //       )
    //       .then(res => res.json())
    //       .then(all_episodes => this.allEpisodes = all_episodes)
    //       // .then(() => this.sortEpisodes("episodeNumber"))
          
    //   });
    // }

    //   Promise.all(promises)
    //     .then(data => {
    //       const episodeData = data.reduce(
    //         (flat, toFlatten) => flat.concat(toFlatten),
    //         []
    //       );
    //       this.allEpisodes = episodeData;
    //     })
    //     .then(() => this.sortEpisodes("episodeNumber"));
    // }

    // getCompleteEpisodeData: function() {
    //   fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=0&pageSize=100&numberOfElements=100")
    //   .then(res => res.json())
    //   .then(episodes_0 => this.allEpisodes.push(this.allEpisodes, episode_0))
    //   .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=1&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_1 => this.allEpisodes.push(this.allEpisodes, episode_1))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=2&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_2 => this.allEpisodes.push(this.allEpisodes, episode_2))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=3&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_3 => this.allEpisodes.push(this.allEpisodes, episode_3))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=4&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_4 => this.allEpisodes.push(this.allEpisodes, episode_4))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=5&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_5 => this.allEpisodes.push(this.allEpisodes, episode_5))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=6&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_6 => this.allEpisodes.push(this.allEpisodes, episode_6))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));

      
      // fetch("http://stapi.co/api/v1/rest/episode/search?pageNumber=7&pageSize=100&numberOfElements=100")
      // .then(res => res.json())
      // .then(episodes_7 => this.allEpisodes.push(this.allEpisodes, episode_7))
      // .then(() => this.sortCompleteEpisodes("episodeNumber"));
    },

    // sortCompleteEpisodes: function(episodeProperty) {
    //   this.allEpisodes.episodes.sort((episodeA, episodeB) => {
    //     return episodeA[episodeProperty] < episodeB[episodeProperty] ? -1 : 1;
    //   });
  //   }
  // },

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
    // this.getCompleteEpisodeData();

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
  text-decoration: underline;
}
.testing {
  color: red;
}

</style>