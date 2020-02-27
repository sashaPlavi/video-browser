<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
      <VideList @videoSelect="onVideoSelect" :videos="videos"></VideList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideList from "./components/VideList";
import VideoDetail from "./components/VideoDetail";
const API_KEY = "AIzaSyBQ020Dv8Mcup_c0UPzsPCU-kq9Dv4xXEE";
export default {
  name: "App",
  components: {
    SearchBar,
    VideList,
    VideoDetail
  },
  data() {
    return { videos: [], selectedVideo: null };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(res => {
          this.videos = res.data.items;
        });
    }
  }
};
</script>

<style>
body {
  background-color: #dddd;
}
</style>
