<template lang="html">
    <div v-if='season'>
        <h2>Season Details:</h2>
        <h3>{{ season.title }}</h3>
        <p>{{ season.numberOfEpisodes }}</p>
        
    </div> 
</template>

<script>
export default {
    name: 'season-details',
    props: ['season']

}
</script>
     
<style lang="css" scoped>

</style>