<template>
  <div>
    <h2>Đăng nhập</h2>
    <p v-if="authState.isAuthenticated">Bạn đã đăng nhập</p>
    <button v-else @click="handleLogin">Đăng nhập</button>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
import { authState } from '../router/index'

const router = useRouter()

const handleLogin = () => {
  authState.isAuthenticated = true;
  alert('Đăng nhập thành công!');
  router.push({ name: 'Dashboard' });
}
</script>