<template lang="html">
    <div>
        <p class="testing">AllEpisodesList.vue</p>
        <ul>
            <all-episodes-list-item
            v-for="(episode, index) in allEpisodes" :episode="episode" :key="index">
            </all-episodes-list-item>
        </ul>
        <hr>
    </div>
</template>

<script>
import AllEpisodesListItem from './AllEpisodesListItem.vue'

export default {
    name: 'all-episodes-list',
    props: ['allEpisodes'],
    components: {
        'all-episodes-list-item': AllEpisodesListItem
    }
}
</script>

<style lang="css" scoped>
.testing {
  color: red;
}
</style>