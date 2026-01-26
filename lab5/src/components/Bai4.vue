<template>
  <div class="bai4-container">
    <h2 class="text-center mb-4">Bài 4: Blog App</h2>
    <CreatePost @add-post="addPost" />
    <hr />
    <PostList :posts="posts" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import CreatePost from './CreatePost.vue';
import PostList from './PostList.vue';

const posts = ref([]);

function addPost(post) {
  posts.value.push(post);
}
</script>

<style scoped>
.bai4-container {
    background-color: #f4f4f4;
    padding: 20px;
    border-radius: 8px;
}
</style>