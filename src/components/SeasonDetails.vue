<template lang="html">
    <div v-if='season'>
        <h2>Season Details:</h2>
        <h3>{{ season.title }}</h3>
        <p>{{ season.numberOfEpisodes }}</p>
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
    props: ['season'],


components: {
    "all-seasons-list": AllSeasonsList,
    "all-episodes-list": AllEpisodesList,
    "all-episodes-list-item": AllEpisodesListItem
}
}
</script>
     
<style lang="css" scoped>

</style>