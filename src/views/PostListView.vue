<template>
    <h1>Listado de posts
    </h1>

    <ul class="post-list">
        <li v-for="post in posts" v-bind:key="post.id">

            <router-link v-bind:to="{ name: 'PostDetail', params: { id: post.id } }">
                {{ post.title }}
            </router-link>

        </li>
    </ul>
</template>

<script lang="ts" setup>
import PostService from '@/services/PostService.ts';
import { onMounted } from 'vue';

const service = new PostService();
const posts = service.getPosts();

onMounted(async () => {
    await service.fetchAll();
})

</script>

<style scoped lang="scss">
.post-list {
    width: 95vh;
    height: 75px;
    padding: 20px;
    list-style-type: none;

    li {
        padding: 10px;
        width: 100%;
        border: 1px solid #ccc;
        color: $primary-color;

        a {
            text-decoration: none;
            color: $primary-color;
            cursor: pointer;
        }

        a:hover {
            color: white;
        }
    }

    li:hover {
        background-color: $primary-color;
        color: white;
    }
}
</style>