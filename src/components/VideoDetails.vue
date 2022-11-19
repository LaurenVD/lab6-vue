<script setup>
    import { ref, onMounted } from 'vue';

    let username = ref("");
    let description = ref("");

    // onMounted
    onMounted(() => {
        const apiUrl = "https://app.fakejson.com/q/Tb9Kbh0b?token=3LVGJEYJ1USZTvt0w9VmZw"
        fetch(apiUrl)
            .then(res => res.json())
            .then(data => {
                username.value = data.videos[0].username;
                description.value = data.videos[0].description;
            })
    })
</script>

<template>
    <div>
        <h2>{{ username }}</h2>
        <p>{{ description }}</p>
    </div>
</template>

<style scoped>
    div {
        padding: 0 2rem;
    }
</style>