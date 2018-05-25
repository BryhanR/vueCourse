<template>
  <ul>
    <videoListItem v-for="video in videos"
      :video=""
    >

    </videoListItem>
  </ul>
</template>


<script>

import videoListItem from './videoListItem';

  export default {
    name: 'videoList',
    props: {
      videos: Array
    },
    components: {
      videoListItem
    }
  }

</script>

<style>

</style>
