<template>
  <div class="container">
    <SearchBar @termChange="onTermChange">
    </SearchBar>
    <div class="row">
      <videoDetail 
        :video="selectedVideo"
      />
      <videoList 
        :videos="videos"
        @videoSelect="onVideoSelect"  
      />
    </div>

  </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import videoList from './components/videoList';
import videoDetail from './components/videoDetail';
import axios from 'axios';

const API_KEY = 'AIzaSyBBSeGRYizCcIEFki_1P_dlfKvtoDT8TQg';

export default {
  name: 'app',
  data () {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    videoList,
    videoDetail
  },
  methods: {
    onTermChange (value) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: value
        }
      }).then( (response) => this.videos = response.data.items );
    },

    onVideoSelect (video) {
      this.selectedVideo = video;
    }
  }
}
</script>

<style>
</style>
