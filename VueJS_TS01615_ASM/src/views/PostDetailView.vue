<script setup>
import { ref, onMounted } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const post = ref(null)
const commentContent = ref('')
const currentUser = ref(null)

const loadPost = () => {
  const posts = JSON.parse(localStorage.getItem('posts') || '[]')
  post.value = posts.find(p => p.id == route.params.id)
}

onMounted(() => {
  loadPost()
  currentUser.value = JSON.parse(localStorage.getItem('currentUser'))
})

const submitComment = () => {
  if (!currentUser.value) {
    alert('Bạn phải đăng nhập để bình luận!')
    return
  }
  
  if (!commentContent.value.trim()) return

  const newComment = {
    user: currentUser.value.username,
    text: commentContent.value,
    date: new Date().toLocaleString()
  }

  if (!post.value.comments) {
    post.value.comments = []
  }
  post.value.comments.push(newComment)
  commentContent.value = ''

  const posts = JSON.parse(localStorage.getItem('posts') || '[]')
  const index = posts.findIndex(p => p.id == post.value.id)
  if (index !== -1) {
    posts[index] = post.value
    localStorage.setItem('posts', JSON.stringify(posts))
  }
}
</script>

<template>
  <div v-if="post" class="row">
    <div class="col-lg-8 mx-auto">
      <h1 class="mb-3">{{ post.title }}</h1>
      <p class="text-muted">Đăng bởi <strong>{{ post.author || 'Admin' }}</strong> vào {{ post.date }}</p>
      
      <img :src="post.image" class="img-fluid rounded mb-4 w-100" alt="Post image">
      
      <div class="content fs-5 mb-5">
        {{ post.content }}
      </div>

      <hr>

      <div class="bg-light p-4 rounded mt-4">
        <h4>Bình luận ({{ post.comments ? post.comments.length : 0 }})</h4>
        
        <div v-if="currentUser" class="mb-3 mt-3">
          <textarea v-model="commentContent" class="form-control" rows="3" placeholder="Chia sẻ ý kiến của bạn..."></textarea>
          <button @click="submitComment" class="btn btn-primary mt-2">Gửi bình luận</button>
        </div>
        <div v-else class="alert alert-warning mt-3">
          Vui lòng <router-link to="/login">đăng nhập</router-link> để bình luận.
        </div>

        <div class="list-group mt-4">
          <div v-for="(comment, index) in post.comments" :key="index" class="list-group-item">
            <div class="d-flex w-100 justify-content-between">
              <h6 class="mb-1 fw-bold text-primary">{{ comment.user }}</h6>
              <small class="text-muted">{{ comment.date }}</small>
            </div>
            <p class="mb-1">{{ comment.text }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div v-else class="text-center mt-5">
    <h3>Không tìm thấy bài viết!</h3>
    <router-link to="/" class="btn btn-secondary">Quay lại trang chủ</router-link>
  </div>
</template>