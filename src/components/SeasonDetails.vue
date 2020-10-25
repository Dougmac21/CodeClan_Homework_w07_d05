<template lang="html">
    <article v-if='season'>
        <h2>Season {{ season.seasonNumber }}</h2>
        <span>Season {{ season.seasonNumber }} </span>
        <span>consisted of {{ season.numberOfEpisodes }} episodes:</span>
        <ul>
            <all-episodes-list-item
            v-if="season.title === episode.season.title"
            v-for="(episode, index) in allEpisodes" :episode="episode" :key="index"
            >
            </all-episodes-list-item>
        </ul>
    </article> 
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

ul {
    list-style: none;
}


</style>

