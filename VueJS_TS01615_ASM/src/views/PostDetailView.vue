<script setup>
import { useRoute } from 'vue-router';
const route = useRoute();
const postId = route.params.id;
</script>

<template>
  <div class="row">
    <div class="col-lg-8 mx-auto">
      <h1 class="mb-3">Tiêu đề bài viết demo {{ postId }}</h1>
      <img src="https://placehold.co/800x400" class="img-fluid rounded mb-4" alt="Post image">
      <p class="lead">Đây là nội dung mô tả ngắn của bài viết...</p>
      <p>Nội dung chi tiết của bài viết</p>
      
      <hr class="my-5">

      <div class="bg-light p-4 rounded">
        <h4>Bình luận</h4>
        
        <div class="mb-3 mt-3">
          <textarea class="form-control" rows="3" placeholder="Viết bình luận của bạn..."></textarea>
          <button class="btn btn-secondary mt-2 btn-sm">Gửi bình luận</button>
        </div>

        <div class="list-group mt-4">
          <div class="list-group-item">
            <div class="d-flex w-100 justify-content-between">
              <h6 class="mb-1 fw-bold">Nguyễn Văn A</h6>
              <small>3 ngày trước</small>
            </div>
            <p class="mb-1">Bài viết rất hữu ích</p>
          </div>
           <div class="list-group-item">
            <div class="d-flex w-100 justify-content-between">
              <h6 class="mb-1 fw-bold">Trần Thị B</h6>
              <small>Vừa xong</small>
            </div>
            <p class="mb-1">Mong chờ bài tiếp theo</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>