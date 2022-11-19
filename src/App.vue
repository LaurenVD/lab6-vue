<script setup>
 // import VideoPlayer.vue
import VideoPlayer from './components/VideoPlayer.vue'
  // import VideoDetails.vue
import VideoDetails from './components/VideoDetails.vue'
</script>

<template>
  <div class="app" >
    <VideoPlayer />
    <VideoDetails />
  </div>
</template>

<style scoped>
.app {
  display: grid;
  grid-template-columns: 8fr 4fr;
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}
</style>