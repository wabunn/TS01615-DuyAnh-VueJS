<script setup>
import { ref, onMounted } from 'vue'

const posts = ref([])

const samplePosts = [
  {
    id: 1,
    title: 'Giới thiệu về Vue.js',
    image: '/images/vuejs.png',
    desc: 'Vue.js là một framework JavaScript tiến bộ dùng để xây dựng giao diện người dùng...',
    content: 'Vue.js (phát âm là /vjuː/, giống như "view") là một framework JavaScript tiến bộ dùng để xây dựng giao diện người dùng. Khác với các framework nguyên khối (monolithic), Vue được thiết kế từ đầu để có thể chấp nhận việc áp dụng dần dần (incrementally adoptable). Lớp nhân của thư viện chỉ tập trung vào view layer, rất dễ để làm quen và tích hợp với các thư viện hoặc dự án có sẵn.',
    author: 'Admin',
    date: '1/02/2026',
    comments: []
  },
  {
    id: 2,
    title: 'Làm quen với Bootstrap 5',
    image: '/images/bootstrap.png',
    desc: 'Bootstrap là bộ công cụ frontend open source phổ biến nhất thế giới...',
    content: 'Bootstrap giúp xây dựng các trang web responsive nhanh chóng. Phiên bản 5 đã loại bỏ sự phụ thuộc vào jQuery và chuyển sang sử dụng Vanilla JavaScript, giúp cải thiện hiệu suất đáng kể. Hệ thống Grid System của Bootstrap cực kỳ mạnh mẽ để chia bố cục trang web.',
    author: 'Duy Anh',
    date: '2/02/2026',
    comments: [
      { user: 'User A', text: 'Bài viết rất hay!', date: '3/02/2026' }
    ]
  },
  {
    id: 3,
    title: 'Hướng dẫn Routing trong Vue',
    image: '/images/router.png',
    desc: 'Vue Router là bộ định tuyến chính thức dành cho Vue.js...',
    content: 'Để tạo một ứng dụng Single Page Application (SPA), chúng ta cần điều hướng giữa các trang mà không cần tải lại trình duyệt. Vue Router làm điều này bằng cách map các URL vào các Component tương ứng.',
    author: 'Admin',
    date: '12/01/2026',
    comments: []
  }
]

onMounted(() => {
  const savedPosts = localStorage.getItem('posts')

  if (savedPosts) {
    posts.value = JSON.parse(savedPosts)
  } else {
    posts.value = samplePosts
    localStorage.setItem('posts', JSON.stringify(samplePosts))
  }
})
</script>

<template>
  <div class="p-5 mb-5 bg-primary rounded-3 text-white text-center shadow-sm" 
       style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);">
    <div class="container-fluid py-3">
      <h1 class="display-5 fw-bold">Chào mừng đến với Blog IT</h1>
      <p class="fs-5 mt-3">Nơi chia sẻ kiến thức lập trình, công nghệ và cuộc sống.</p>
      <router-link to="/create-post" class="btn btn-light btn-lg mt-3 shadow">
        <i class="bi bi-pencil-fill"></i> Viết bài ngay
      </router-link>
    </div>
  </div>

  <div class="container">
    <h3 class="mb-4 fw-bold text-dark border-start border-4 border-primary ps-3">Bài Viết Mới Nhất</h3>
    
    <div class="row">
      <div v-if="posts.length === 0" class="col-12 text-center text-muted mt-5">
         <p>Đang tải dữ liệu hoặc chưa có bài viết...</p>
      </div>

      <div class="col-md-4 mb-4" v-for="post in posts" :key="post.id">
        <div class="card h-100 shadow-sm post-card">
          <img :src="post.image" class="card-img-top" alt="...">
          <div class="card-body d-flex flex-column">
            <div class="mb-2">
              <span class="badge bg-light text-dark border">{{ post.author || 'Admin' }}</span>
              <span class="text-muted small ms-2">{{ post.date }}</span>
            </div>
            
            <h5 class="card-title fw-bold text-dark">{{ post.title }}</h5>
            <p class="card-text text-secondary small flex-grow-1">{{ post.desc }}</p>
            
            <div class="mt-3 pt-3 border-top">
               <router-link :to="`/post/${post.id}`" class="btn btn-outline-primary btn-sm w-100">
                 Đọc tiếp →
               </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-img-top {
  width: 100%;
  height: 200px;
  object-fit: cover;
  object-position: center;
}

.card {
  height: 100%;
}
</style>