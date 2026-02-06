<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const username = ref('')
const email = ref('')
const password = ref('')

const handleRegister = () => {
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  if (users.find(u => u.email === email.value)) {
    alert('Email này đã được sử dụng!')
    return
  }
  const newUser = {
    id: Date.now(),
    username: username.value,
    email: email.value,
    password: password.value,
    avatar: 'https://placehold.co/150'
  }
  users.push(newUser)
  localStorage.setItem('users', JSON.stringify(users))
  alert('Đăng ký thành công! Vui lòng đăng nhập.')
  router.push('/login')
}
</script>

<template>
  <div class="d-flex align-items-center justify-content-center min-vh-75">
    <div class="card border-0 shadow-lg rounded-4 p-4" style="width: 100%; max-width: 500px;">
      <div class="card-body">
        <div class="text-center mb-4">
          <h3 class="fw-bold text-success">Tạo Tài Khoản</h3>
          <p class="text-muted">Tham gia cộng đồng ngay hôm nay</p>
        </div>

        <form @submit.prevent="handleRegister">
          <div class="form-floating mb-3">
            <input v-model="username" type="text" class="form-control rounded-3" id="regName" placeholder="Tên" required>
            <label for="regName">Tên hiển thị</label>
          </div>
          
          <div class="form-floating mb-3">
            <input v-model="email" type="email" class="form-control rounded-3" id="regEmail" placeholder="Email" required>
            <label for="regEmail">Email</label>
          </div>

          <div class="form-floating mb-4">
            <input v-model="password" type="password" class="form-control rounded-3" id="regPass" placeholder="Pass" required>
            <label for="regPass">Mật khẩu</label>
          </div>

          <button class="btn btn-success w-100 py-3 rounded-pill fw-bold shadow-sm transition-btn">
            Đăng Ký
          </button>
        </form>
        
        <div class="text-center mt-4">
          <small class="text-muted">Đã có tài khoản? <router-link to="/login" class="fw-bold text-success">Đăng nhập</router-link></small>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.transition-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(25, 135, 84, 0.3);
}
</style>