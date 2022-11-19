<script setup>
 // import VideoPlayer.vue
import VideoPlayer from './components/VideoPlayer.vue'
  // import VideoDetails.vue
import VideoDetails from './components/VideoDetails.vue'
  // import Comment.vue
import Comment from './components/Comment.vue'
</script>

<template>
  <div class="app" >
    <VideoPlayer />
    <div class="details">
      <VideoDetails />
      <Comment />
    </div>
  </div>
</template>

<style scoped>
.app {
  display: grid;
  grid-template-columns: 8fr 4fr;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.details {
  padding-right: 2rem;
}
</style>