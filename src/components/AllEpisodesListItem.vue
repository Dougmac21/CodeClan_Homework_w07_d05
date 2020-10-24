<template>
  <div>
        <ul>
            <li
            
            v-on:click='handleClick'
            >
            <h2>{{ episode.title }}</h2>
            <p>{{ episode.synopsis }}</p>
            </li>
        </ul>
  </div>
</template>

<script>
import {eventBus} from '@/main.js';

export default {
    name: 'all-episodes-list-item',
    props: ['episode'],
    methods: {
        handleClick() {
            eventBus.$emit('episode-selected', this.episode)
        }
    }
}
</script>

<style land="css" scoped>
ul {
    list-style: none;
    cursor: pointer;
}
</style>