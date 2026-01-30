<template>
  <div class="container mt-5">
    <h3>Nhập điểm của bạn:</h3>
    <input type="number" class="form-control" v-model.number="score" placeholder="Nhập điểm..." min="0" max="10" />

    <div class="mt-3 alert alert-info" v-if="score !== null">
      <h5 v-if="score < 5.0">Xếp loại: Yếu</h5>
      <h5 v-else-if="score < 6.5">Xếp loại: Trung bình</h5>
      <h5 v-else-if="score < 8.0">Xếp loại: Khá</h5>
      <h5 v-else-if="score < 9.0">Xếp loại: Giỏi</h5>
      <h5 v-else>Xếp loại: Xuất sắc</h5>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const score = ref(null);
</script>