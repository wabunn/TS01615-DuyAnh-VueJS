<template>
  <div class="container mt-5">
    <h3>Nhập tháng của bạn:</h3>
    <input type="number" class="form-control" v-model.number="month" placeholder="Nhập tháng (1-12)" />

    <div class="mt-3">
        <p v-if="month < 1 || month > 12" style="color: red">
            Vui lòng nhập tháng từ 1 đến 12
        </p>
        
        <p v-else-if="month <= 3" class="text-success fw-bold">Mùa Xuân</p>
        <p v-else-if="month <= 6" class="text-danger fw-bold">Mùa Hè</p>
        <p v-else-if="month <= 9" class="text-warning fw-bold">Mùa Thu</p>
        <p v-else class="text-primary fw-bold">Mùa Đông</p>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const month = ref(1);
</script>