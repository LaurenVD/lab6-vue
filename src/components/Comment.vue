<script setup>
    import { ref, onMounted, reactive } from 'vue';

    let messages = reactive({messages: []});
    let text = ref("");
    let user = ref("");

    // onMounted
    onMounted(() => {
        const apiUrl = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(apiUrl)
            .then(res => res.json())
            .then(data => {
                messages.messages = data;
            })
    });

    const addComment = () => {

        let myMessage = {
            text: text.value,
            user: "Lauren"
        }

        const apiUrl = "https://lab5-p379.onrender.com/api/v1/messages/";
        fetch(apiUrl, {
            method: "POST",
            headers: {
                "Content-Type": "application/json"
            },
            body: JSON.stringify(myMessage)
        })
        .then(res => res.json())
        .then(data => {
            messages.messages.push({
                text: data.data.text,
                user: data.data.user
            })
        })
    }

</script>

<template>
    <div class="comments">
        <ul>
            <li v-for="message in messages.messages" :key="message.id">
                <h3>{{ message.user }}</h3>
                <p>{{ message.text }}</p>
            </li>
        </ul>
        <input type="text" v-model="text">
        <button @click="addComment">Add Comment</button>
    </div>
</template>

<style scoped>
    div {
        padding: 0 2rem;
    }

    .comments {
        display: flex;
        flex-direction: column;
    }
</style>