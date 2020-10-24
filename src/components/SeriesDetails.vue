<template lang="html">
  <div v-if='series'>
    <h2>Series Details:</h2>
    <h3>{{ series.title }}</h3>
    <p> Ran for {{ series.seasonsCount }} seasons.</p>
    <p> Over {{ series.episodesCount }} episodes.</p>
    <all-seasons-list :allSeasons='allSeasons'></all-seasons-list>


  </div>

</template>

<script>

import AllSeasonsList from './AllSeasonsList';


export default {
 name: 'series-details',
 props: ['series', 'allSeasons'],


components: {
    "all-seasons-list": AllSeasonsList
}
}
</script>

<style lang="css" scoped>

</style>