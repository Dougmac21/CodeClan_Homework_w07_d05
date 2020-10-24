<template lang="html">
  <div v-if='series'>
    <h2>Series Details:</h2>
    <h3>{{ series.title }}</h3>
    <p> Ran for {{ series.seasonsCount }} seasons.</p>
    <p> Over {{ series.episodesCount }} episodes.</p>

  </div>

</template>

<script>
export default {
 name: 'series-details',
 props: ['series']
}
</script>

<style lang="css" scoped>

</style>