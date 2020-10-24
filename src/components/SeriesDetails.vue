<template lang="html">
    <div v-if='series'>
        <h2>{{ series.title }}</h2>
        <p> Total of {{ series.episodesCount }} episodes</p>
        <p> over {{ series.seasonsCount }} seasons.</p>
        <all-seasons-list-item
        v-if="season.series.title === series.title"
        v-for="(season, index) in allSeasons" :season="season" :key="index">
        </all-seasons-list-item>
    </div>

</template>

<script>
import AllSeriesList from './AllSeriesList'
import AllSeasonsList from './AllSeasonsList';
import AllSeasonsListItem from './AllSeasonsListItem';


export default {
 name: 'series-details',
 props: ['series', 'allSeasons'],


components: {
    "all-series-list": AllSeriesList,
    "all-seasons-list": AllSeasonsList,
    "all-seasons-list-item": AllSeasonsListItem
}
}
</script>

<style lang="css" scoped>

</style>