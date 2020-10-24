<template lang="html">
    <div v-if='season'>
        <h2>SeasonDetails.vue</h2>
        <p>{{ season.numberOfEpisodes }} episodes XXXXX</p>

        <all-episodes-list-item
        
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

</style>

        // v-if="episode.season.title === season.title"
