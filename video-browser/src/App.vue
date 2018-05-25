<template>
  <div>
    <SearchBar @termChange="onTermChange">
    </SearchBar>
    <videoList :videos="videos"></videoList>
    {{ videos.length }}
  </div>
</template>

<script>
import SearchBar from './components/SearchBar';
import videoList from './components/videoList';
import axios from 'axios';

const API_KEY = 'AIzaSyBBSeGRYizCcIEFki_1P_dlfKvtoDT8TQg';

export default {
  name: 'app',
  data () {
    return {
      videos: []
    };
  },
  components: {
    SearchBar,
    videoList
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
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
