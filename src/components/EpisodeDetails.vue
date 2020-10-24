<template lang="html">
    <div v-if='episode'>
        <h2>Episode Detail:</h2>
        <h3>{{ episode.title }}</h3>
        <p>{{ episode.plot }}</p>
    </div>
</template>

<script>
export default {
    name: 'episode-details',
    props: ['episode']
}
</script>

<style lang="css" scoped>


</style>