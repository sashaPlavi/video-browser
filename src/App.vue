<template>
  <div id="app">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideList :videos="videos"></VideList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar.vue";
import VideList from "./components/VideList";
const API_KEY = "AIzaSyBQ020Dv8Mcup_c0UPzsPCU-kq9Dv4xXEE";
export default {
  name: "App",
  components: {
    SearchBar,
    VideList
  },
  data() {
    return { videos: [] };
  },
  methods: {
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
