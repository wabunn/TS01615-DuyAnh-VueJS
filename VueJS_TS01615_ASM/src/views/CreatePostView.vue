<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const title = ref('')
const image = ref('')
const content = ref('')

const handleCreatePost = () => {
  const currentUser = JSON.parse(localStorage.getItem('currentUser'))
  if (!currentUser) {
    alert('Vui lòng đăng nhập!')
    router.push('/login')
    return
  }
  const posts = JSON.parse(localStorage.getItem('posts') || '[]')
  const newPost = {
    id: Date.now(),
    title: title.value,
    image: image.value || 'https://placehold.co/600x400',
    desc: content.value.substring(0, 100) + '...',
    content: content.value,
    author: currentUser.username,
    date: new Date().toLocaleDateString(),
    comments: []
  }
  posts.unshift(newPost)
  localStorage.setItem('posts', JSON.stringify(posts))
  alert('Đăng bài thành công!')
  router.push('/')
}
</script>

<template>
  <div class="container" style="max-width: 800px;">
    <div class="card border-0 shadow-sm rounded-4">
      <div class="card-body p-5">
        <h3 class="fw-bold mb-4 text-dark border-start border-5 border-primary ps-3">Viết Bài Mới</h3>
        
        <form @submit.prevent="handleCreatePost">
          <div class="mb-4">
            <label class="form-label fw-bold text-secondary">Tiêu đề bài viết</label>
            <input v-model="title" type="text" class="form-control form-control-lg rounded-3 bg-light border-0" placeholder="Nhập tiêu đề hấp dẫn..." required>
          </div>

          <div class="mb-4">
            <label class="form-label fw-bold text-secondary">Link hình ảnh (URL)</label>
            <div class="input-group">
              <span class="input-group-text bg-light border-0"><i class="bi bi-image"></i></span>
              <input v-model="image" type="text" class="form-control bg-light border-0" placeholder="https://...">
            </div>
            <small class="text-muted fst-italic">* Để trống sẽ dùng ảnh mặc định</small>
          </div>

          <div class="mb-4">
            <label class="form-label fw-bold text-secondary">Nội dung</label>
            <textarea v-model="content" class="form-control bg-light border-0 rounded-3" rows="8" placeholder="Chia sẻ câu chuyện của bạn..." required></textarea>
          </div>

          <div class="d-flex justify-content-end gap-2">
            <router-link to="/" class="btn btn-light rounded-pill px-4">Hủy</router-link>
            <button class="btn btn-primary rounded-pill px-5 fw-bold shadow-sm">Đăng Bài</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
.form-control:focus {
  box-shadow: none;
  background-color: #fff;
  border: 1px solid #cfe2ff !important;
}
</style>