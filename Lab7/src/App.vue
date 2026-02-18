<template>
  <div class="container py-4">
    <h1 class="text-center text-primary mb-4 fw-bold">1_TS01615_Do Duy Anh_Lab 7</h1>

    <nav class="d-flex justify-content-center gap-3 mb-4">
      <router-link to="/bai1" class="btn btn-outline-primary" active-class="active">Bài 1</router-link>
      <router-link to="/bai2" class="btn btn-outline-primary" active-class="active">Bài 2</router-link>
      <router-link to="/bai3" class="btn btn-outline-primary" active-class="active">Bài 3</router-link>
      <router-link to="/bai4" class="btn btn-outline-primary" active-class="active">Bài 4</router-link>
    </nav>

    <div class="card shadow-sm">
      <div class="card-body">
        <router-view></router-view>
      </div>
    </div>
  </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<style>
.btn-outline-primary.active {
  background-color: #0d6efd;
  color: white;
}
</style>