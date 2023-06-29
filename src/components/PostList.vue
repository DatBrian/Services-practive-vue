<template>
    <h1>Listado de posts
        <button class="btn btn-primary">Estilado con bootstrap</button>
    </h1>

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

<style scoped lang="scss">
.post-list {
    width: 95vh;
    height: 75px;
    padding: 20rem;
    list-style-type: none;

    li {
        padding: 10px;
        width: 100%;
        border: 1px solid #ccc;
        color: $red;
    }

    li:hover {
        background-color: darken($color: #000000, $amount: 10%);
    }
}
</style>