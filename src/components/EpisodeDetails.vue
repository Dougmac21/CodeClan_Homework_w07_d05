<template lang="html">
    <div v-if='episode'>
        <h2>{{ episode.series.title }}</h2>
            <ul>
            <span>Season {{ episode.seasonNumber }}- Episode {{ episode.episodeNumber }}: </span>
            <span>{{ episode.title }}</span>
            <p>Original Airdate: {{ episode.usAirDate }}</p>
            </ul>




    </div>
</template>

<script>
import AllSeasonsList from './AllSeasonsList';
import AllEpisodesList from './AllEpisodesList';
import AllEpisodesListItem from './AllEpisodesListItem';


export default {
    name: 'episode-details',
    props: ['episode'],


components: {
    "all-seasons-list": AllSeasonsList,
    "all-episodes-list": AllEpisodesList,
    "all-episodes-list-item": AllEpisodesListItem
}
}
</script>

<style lang="css" scoped>
.testing {
  color: red;
}
</style>