<script setup>
import { ref } from 'vue'

const posts = ref([
  { id: 1, title: 'Làm quen với Vue.js', desc: 'Giới thiệu các khái niệm cơ bản...', image: 'https://placehold.co/600x400' },
  { id: 2, title: 'Bootstrap 5 có gì mới?', desc: 'Tìm hiểu các tính năng mới trong BS5...', image: 'https://placehold.co/600x400' },
  { id: 3, title: 'Hướng dẫn Routing', desc: 'Cách sử dụng Vue Router hiệu quả...', image: 'https://placehold.co/600x400' }
])
</script>

<template>
  <h2 class="mb-4">Bài viết mới nhất</h2>
  <div class="row">
    <div class="col-md-4 mb-4" v-for="post in posts" :key="post.id">
      <div class="card h-100 shadow-sm">
        <img :src="post.image" class="card-img-top" alt="...">
        <div class="card-body">
          <h5 class="card-title">{{ post.title }}</h5>
          <p class="card-text">{{ post.desc }}</p>
          <RouterLink :to="{ name: 'post-detail', params: { id: post.id } }" class="btn btn-primary btn-sm">Xem chi tiết</RouterLink>
        </div>
      </div>
    </div>
  </div>
</template>