<script setup>
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const user = ref(null)

onMounted(() => {
  const savedUser = localStorage.getItem('currentUser')
  if (savedUser) {
    user.value = JSON.parse(savedUser)
  } else {
    router.push('/login')
  }
})

const handleUpdate = () => {
  localStorage.setItem('currentUser', JSON.stringify(user.value))
  const users = JSON.parse(localStorage.getItem('users') || '[]')
  const index = users.findIndex(u => u.email === user.value.email)
  if (index !== -1) {
    users[index] = user.value
    localStorage.setItem('users', JSON.stringify(users))
  }
  alert('Đã cập nhật hồ sơ!')
}

const handleLogout = () => {
  localStorage.removeItem('currentUser')
  router.push('/login')
}
</script>

<template>
  <div v-if="user" class="container">
    <div class="position-relative mb-5">
      <div class="rounded-4 overflow-hidden shadow-sm" style="height: 200px; background: linear-gradient(to right, #4facfe 0%, #00f2fe 100%);"></div>
      
      <div class="position-absolute top-100 start-50 translate-middle text-center">
        <img :src="user.avatar" class="rounded-circle border border-4 border-white shadow" width="120" height="120" style="object-fit: cover; background: #fff;">
        <h4 class="mt-2 fw-bold mb-0">{{ user.username }}</h4>
        <span class="badge bg-secondary rounded-pill">{{ user.email }}</span>
      </div>
    </div>

    <div class="row justify-content-center mt-5 pt-4">
      <div class="col-md-8">
        <div class="card border-0 shadow-sm rounded-4">
          <div class="card-header bg-white border-0 pt-4 px-4">
            <h5 class="fw-bold text-primary"><i class="bi bi-gear-fill me-2"></i>Cài đặt tài khoản</h5>
          </div>
          <div class="card-body p-4">
            <form @submit.prevent="handleUpdate">
              <div class="row">
                <div class="col-md-6 mb-3">
                  <label class="form-label text-muted small fw-bold">TÊN HIỂN THỊ</label>
                  <input v-model="user.username" type="text" class="form-control rounded-3">
                </div>
                <div class="col-md-6 mb-3">
                  <label class="form-label text-muted small fw-bold">EMAIL (Không đổi)</label>
                  <input v-model="user.email" type="email" class="form-control rounded-3 bg-light" disabled>
                </div>
              </div>

              <div class="mb-3">
                <label class="form-label text-muted small fw-bold">LINK AVATAR</label>
                <input v-model="user.avatar" type="text" class="form-control rounded-3">
              </div>

              <div class="mb-4">
                <label class="form-label text-muted small fw-bold">MẬT KHẨU MỚI</label>
                <input v-model="user.password" type="password" class="form-control rounded-3">
              </div>

              <div class="d-flex justify-content-between align-items-center">
                <button type="button" @click="handleLogout" class="btn btn-outline-danger rounded-pill px-4">
                  <i class="bi bi-box-arrow-right"></i> Đăng xuất
                </button>
                <button class="btn btn-primary rounded-pill px-4 shadow-sm fw-bold">
                  <i class="bi bi-save"></i> Lưu thay đổi
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>