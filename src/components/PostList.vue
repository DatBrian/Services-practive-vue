<template>
    <h1>Listado de posts</h1>

    <ul class="post-list">
        <li v-for="post in posts" v-bind:key="post.id">{{ post.title }}</li>
    </ul>
</template>

<script lang="ts" setup>
import PostService from '@/services/PostServices';
import { onMounted } from 'vue';

const service = new PostService();
const posts = service.getPosts();

onMounted(async () => {
    await service.fetchAll();
})

</script>

<style scoped>
.post-list {
    width: 95vh;
    height: 8rem;
    padding: 1.3rem;
    list-style-type: none;
}

.post-list{
    padding: .8rem;
    width: 100%;
    border: 1px solid #ccc;
}
</style>