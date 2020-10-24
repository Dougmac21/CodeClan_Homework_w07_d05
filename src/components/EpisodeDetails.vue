<template lang="html">
    <div v-if='episode'>
        <h2>{{ episode.title }}</h2>
        <p class="testing">EpisodeDetails.vue</p>





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