<template>
  <ul class="list-group col-md-4">
    <videoListItem 
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
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
    },
    methods: {
      onVideoSelect (video) {
        this.$emit('videoSelect', video)
      }
    }
  }

</script>

<style>

</style>
