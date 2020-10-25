<template lang="html">
    <div v-if='episode'>
        <h2>{{ episode.series.title }}</h2>
        <span>Season {{ episode.seasonNumber }}- Episode {{ episode.episodeNumber }}: </span>
        <span>{{ episode.title }}</span>
        <ul>
            <span>Originally airing on: {{ episode.usAirDate }}, </span>
            <span>this episodes events took place between Stardate {{ episode.stardateFrom }} and Stardate {{ episode.stardateTo }}</span>
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