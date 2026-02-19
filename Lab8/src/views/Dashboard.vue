<template>
  <div>
    <h2>Bảng điều khiển</h2>
    <p>Chào mừng bạn. Đây là khu vực dành riêng cho người dùng đã xác thực.</p>
    <button @click="handleLogout">Đăng xuất</button>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { authState } from '../router/index'

const router = useRouter()

const handleLogout = () => {
  authState.isAuthenticated = false;
  router.push({ name: 'Login' });
}
</script>