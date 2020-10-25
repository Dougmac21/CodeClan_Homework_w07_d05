<template lang="html">
    <article v-if='series'>
        <h2>{{ series.title }}</h2>
        <span> Ran for a total of {{ series.episodesCount }} episodes</span>
        <span> over {{ series.seasonsCount }} seasons.</span>
        <ul>
            <all-seasons-list-item
            v-if="season.series.title === series.title"
            v-for="(season, index) in allSeasons" :season="season" :key="index"
            >
            </all-seasons-list-item>
        </ul>
    </article>
</template>

<script>
import AllSeriesList from './AllSeriesList';
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





.testing {
  color: red;
}
</style>