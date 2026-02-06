<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const email = ref('')
const password = ref('')

const handleLogin = () => {
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const user = users.find(u => u.email === email.value && u.password === password.value)

  if (user) {
    localStorage.setItem('currentUser', JSON.stringify(user))
    alert('Đăng nhập thành công! Chào mừng trở lại.')
    router.push('/')
  } else {
    alert('Email hoặc mật khẩu không đúng!')
  }
}
</script>

<template>
  <div class="d-flex align-items-center justify-content-center min-vh-75">
    <div class="card border-0 shadow-lg rounded-4 overflow-hidden" style="max-width: 900px; width: 100%;">
      <div class="row g-0">
        
        <div class="col-lg-6 d-none d-lg-block bg-login-image">
          <div class="overlay"></div>

          <div class="scrolling-content">
            <div class="tech-group">
              <h2 class="tech-text">Vue.js 3</h2>
              <h2 class="tech-text">Bootstrap 5</h2>
              <h2 class="tech-text">JavaScript</h2>
              <h2 class="tech-text">TypeScript</h2>
              <h2 class="tech-text">Vite Build</h2>
              <h2 class="tech-text">Responsive</h2>
              <h2 class="tech-text">Clean UI</h2>
              <h2 class="tech-text">Frontend</h2>
            </div>

            <div class="tech-group">
              <h2 class="tech-text">Vue.js 3</h2>
              <h2 class="tech-text">Bootstrap 5</h2>
              <h2 class="tech-text">JavaScript</h2>
              <h2 class="tech-text">TypeScript</h2>
              <h2 class="tech-text">Vite Build</h2>
              <h2 class="tech-text">Responsive</h2>
              <h2 class="tech-text">Clean UI</h2>
              <h2 class="tech-text">Frontend</h2>
            </div>
          </div>
        </div>
        
        <div class="col-lg-6 p-5 bg-white">
          <div class="text-center mb-4">
            <h2 class="fw-bold text-primary">Chào Mừng</h2>
            <p class="text-muted">Đăng nhập để khám phá các bài viết thú vị</p>
          </div>
          
          <form @submit.prevent="handleLogin">
            <div class="form-floating mb-3">
              <input v-model="email" type="email" class="form-control rounded-3" id="floatingInput" placeholder="name@example.com" required>
              <label for="floatingInput">Địa chỉ Email</label>
            </div>
            <div class="form-floating mb-4">
              <input v-model="password" type="password" class="form-control rounded-3" id="floatingPassword" placeholder="Password" required>
              <label for="floatingPassword">Mật khẩu</label>
            </div>
            
            <button class="btn btn-primary w-100 py-3 rounded-pill fw-bold shadow-sm transition-btn">
              Đăng Nhập
            </button>
            
            <div class="text-center mt-4">
              <span class="text-muted">Chưa có tài khoản? </span>
              <router-link to="/register" class="text-decoration-none fw-bold">Đăng ký ngay</router-link>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.bg-login-image {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  position: relative;
  overflow: hidden;
  height: 600px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.scrolling-content {
  position: absolute;
  top: 0;
  width: 100%;
  animation: scrollInfinite 20s linear infinite;
}

@keyframes scrollInfinite {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-50%);
  }
}

.tech-group {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-around;
  padding-bottom: 0; 
}

.tech-text {
  font-family: 'Poppins', sans-serif;
  font-size: 2rem;
  font-weight: 800;
  color: rgba(255, 255, 255, 0.1);
  margin-bottom: 40px;
  text-transform: uppercase;
  letter-spacing: 2px;
  user-select: none;
}

.transition-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(13, 110, 253, 0.3);
}
</style>