<template>
  <li>
    {{ video.snippet.title }}
  </li>
</template>

<script>

export default {
  name: 'videoListItem',
  props:{
    video: Object
  }
};

</script>
