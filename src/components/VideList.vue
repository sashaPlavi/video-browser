<template>
  <ul>
    <VideoListItem
      v-for="(video, ind) in videos"
      v-bind:video="video"
      v-bind:key="ind"
    >
    </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideList",
  components: {
    VideoListItem
  },
  props: {
    videos: Array
  }
};
</script>

<style scoped></style>
