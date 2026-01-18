<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">
        <RouterLink class="navbar-brand" to="/">ASM VueJS</RouterLink>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <RouterLink class="nav-link" to="/create-post">Đăng bài</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="nav-link" to="/profile">Tài khoản</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="btn btn-outline-light ms-2" to="/login">Đăng nhập</RouterLink>
            </li>
            <li class="nav-item">
              <RouterLink class="btn btn-primary ms-2" to="/register">Đăng ký</RouterLink>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>

  <main class="container mt-4 mb-5">
    <RouterView />
  </main>

  <footer class="bg-light text-center py-3 mt-auto">
    <div class="container">
      <p class="text-muted mb-0">TS01615_Assignment_VueJS</p>
    </div>
  </footer>
</template>