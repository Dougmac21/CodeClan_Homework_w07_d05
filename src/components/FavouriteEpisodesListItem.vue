<template>
    <div>
        <li
        
        v-on:click='handleAddFavClick'
        >
        <span> id="fav-episode">Placeholder Text</span>
        </li>











    </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'favourite-episodes-list-item',
    props: ['episode'],
    methods: {
        handleAddFavClick() {
            eventbus.$emit('favourite-selected', this.episode)
        }
    }
}
</script>

<style lang="css" scoped>

li {
    cursor: pointer;
}

</style>