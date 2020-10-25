<template lang="html">
  <div>
        <ul>
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
ul {
    list-style: none;
    padding-left: 0;
    height: 90vh;
    overflow-y: auto;
}


.testing {
  color: red;
}

</style>