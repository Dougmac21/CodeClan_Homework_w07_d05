<template lang="html">
    <div v-if='season'>
        <h2>{{ season.series.title }}</h2>
        <span>Season { season.seasonNumber }}</span>
        <span>Ran for {{ season.numberOfEpisodes }} episodes.</span>
        <ul>
            <all-episodes-list-item

            v-for="(episode, index) in allEpisodes" :episode="episode" :key="index"
            >
            </all-episodes-list-item>
        </ul>
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

        // v-if="season.title === episode.title"
