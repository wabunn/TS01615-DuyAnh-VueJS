<template>
  <div>
    <h2>Danh sách bài viết</h2>
    <ul>
      <li><router-link :to="{ name: 'BlogPost', params: { id: 1 } }">Bài viết 1: Lập trình Vue.js</router-link></li>
      <li><router-link :to="{ name: 'BlogPost', params: { id: 2 } }">Bài viết 2: Vue Router toàn tập</router-link></li>
    </ul>
  </div>
</template>