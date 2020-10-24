<template lang="html">
    <div v-if='series'>
        <h2>{{ series.title }}</h2>
        <p> Ran for {{ series.seasonsCount }} seasons.</p>
        <p> Over {{ series.episodesCount }} episodes.</p>
        <all-seasons-list-item
        v-for="(season, index) in allSeasons" :season="season" :key="index">
        </all-seasons-list-item>
  </div>

</template>

<script>

import AllSeasonsList from './AllSeasonsList';
import AllSeasonsListItem from './AllSeasonsListItem';


export default {
 name: 'series-details',
 props: ['series', 'allSeasons'],


components: {
    "all-seasons-list": AllSeasonsList,
    "all-seasons-list-item": AllSeasonsListItem
}
}
</script>

<style lang="css" scoped>

</style>