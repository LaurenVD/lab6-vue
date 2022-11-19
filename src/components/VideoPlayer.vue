<script setup>
    import { ref, onMounted, reactive } from 'vue'
    import 'animate.css'

    let videos = reactive({data: []});
    let videoSrc = ref("");
    let counter = ref(0);
    let animation = ref("");

    // onMounted
    onMounted(() => {
        const apiUrl = "https://app.fakejson.com/q/Tb9Kbh0b?token=3LVGJEYJ1USZTvt0w9VmZw";
        fetch(apiUrl)
            .then(res => res.json())
            .then(data => {
                videos.data = data.videos;
                videoSrc.value = data.videos[0].video;
            })
    });

    const nextVideo = () => {
        animation.value = "animate__fadeOut";
        counter.value++;
        setTimeout(() => {
            videoSrc.value = videos.data[counter.value].video;
            animation.value = "animate__fadeIn";
        }, 500);
    }
</script>

<template>
    <div class="blur">
        <div class="controls">
            <a @click.prevent="nextVideo" href="#">-></a>
        </div>
        <video 
        :src="videoSrc"
        :class="animation"
        class="animate__animated"
        controls
        autoplay
        muted
        ></video>
    </div>
</template>

<style scoped>
    video {
        max-width: 100%;
        max-height: 100vh;
    }
    .blur {
        background-size: cover;
        text-align: center;
    }

    .controls {
        position: absolute;
        top: 0;
        right: 0;
        height: 100%;
        width: 100%;
        font-size: 2rem;
    }
</style>