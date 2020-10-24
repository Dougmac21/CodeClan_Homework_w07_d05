<template lang="html">
    <div v-if='season'>
        <h2>{{ season.numberOfEpisodes }} episodes</h2>

        <all-episodes-list-item
        v-if="series.title === episode.series.title"
        v-for="(episode, index) in allEpisodes" :episode="episode" :key="index">
        </all-episodes-list-item>
    </div> 
</template>

<script>
import AllSeasonsList from './AllSeasonsList';
import AllEpisodesList from './AllEpisodesList';
import AllEpisodesListItem from './AllEpisodesListItem';


export default {
    name: 'season-details',
    props: ['season', 'allEpisodes'],


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

        // v-if="episode.season.title === season.title"
