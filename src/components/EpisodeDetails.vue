<template lang="html">
    <div v-if='episode'>
        <h2>{{ episode.series.title }}</h2>
        <span>Season {{ episode.seasonNumber }}- Episode {{ episode.episodeNumber }}: </span>
        <span>{{ episode.title }}</span>
        <ul>
            <span>This episode originally aired on: {{ episode.usAirDate }}, </span>
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

</style>