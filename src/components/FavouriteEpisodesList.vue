<template lang="html">
    <div>
        <ul>
            <favourite-episodes-list-item
            v-for="(episode, index) in allEpisodes" :episode="episode" :key="index">
            </favourite-episodes-list-item>
        </ul>
        <hr>
    </div>
</template>

<script>
import FavouriteEpisodesListItem from './FavouriteEpisodesListItem.vue'

export default {
    name: 'favourite-episodes-list',
    props: ['allEpisodes'],
    components: {
        'favourite-episodes-list-item': FavouriteEpisodesListItem
    }
}
</script>

<style lang="css" scoped>

ul {
    list-style: none;
}

</style>