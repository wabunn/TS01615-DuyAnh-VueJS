<template>
  <div>
    <h2>Chi tiết bài viết</h2>
    <p>Bạn đang xem nội dung của bài viết có ID: <strong>{{ $route.params.id }}</strong></p>
    <button @click="goBack">Quay lại danh sách</button>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'
const router = useRouter()

const goBack = () => {
  router.push({ name: 'BlogList' })
}
</script>