<template lang="html">
  <div>
      <h2>Select A Season:</h2>
      <ul>
          <all-seasons-list-item v-for="(season, index) in allSeasons" :season="season" :key="index"></all-seasons-list-item>
      </ul>
  </div>
</template>

<script>
import AllSeasonsListItem from './AllSeasonsListItem.vue'

export default {
    name: 'all-seasons-list',
    props: ['allSeasons'],
    components: {
        'all-seasons-list-item': AllSeasonsListItem
    }
}
</script>

<style>

</style>