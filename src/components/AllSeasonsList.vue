<template lang="html">
  <div>
      <ul>
          <p class="testing">AllSeasonsList.vue</p>
          <all-seasons-list-item
          v-for="(season, index) in allSeasons" :season="season" :key="index">
          </all-seasons-list-item>
      </ul>
      <hr>
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

<style lang="css" scoped>
.testing {
  color: red;
}
</style>