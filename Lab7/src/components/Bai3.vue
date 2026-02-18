<template>
  <div class="p-3">
    <div class="row">
      <div class="col-md-6">
        <h3 class="text-primary">Form Đăng Ký</h3>
        <form @submit.prevent="register">
          <div class="mb-3">
            <label class="form-label">Họ tên:</label>
            <input type="text" class="form-control" v-model="form.name" placeholder="Nhập họ tên">
          </div>
          <div class="mb-3">
            <label class="form-label">Email:</label>
            <input type="email" class="form-control" v-model="form.email" placeholder="Nhập email">
          </div>
          <div class="mb-3">
            <label class="form-label">Mật khẩu:</label>
            <input type="password" class="form-control" v-model="form.password" placeholder="Nhập mật khẩu">
          </div>
          <div class="mb-3">
            <label class="form-label">Ngày sinh:</label>
            <input type="date" class="form-control" v-model="form.dob">
          </div>
          
          <div class="mb-3">
            <label class="form-label d-block">Giới tính:</label>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="radio" value="Nam" v-model="form.gender">
              <label class="form-check-label">Nam</label>
            </div>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="radio" value="Nữ" v-model="form.gender">
              <label class="form-check-label">Nữ</label>
            </div>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="radio" value="Khác" v-model="form.gender">
              <label class="form-check-label">Khác</label>
            </div>
          </div>

          <div class="mb-3">
            <label class="form-label d-block">Ngôn ngữ:</label>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="checkbox" value="Tiếng Việt" v-model="form.languages">
              <label class="form-check-label">Tiếng Việt</label>
            </div>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="checkbox" value="Tiếng Anh" v-model="form.languages">
              <label class="form-check-label">Tiếng Anh</label>
            </div>
            <div class="form-check form-check-inline">
              <input class="form-check-input" type="checkbox" value="Tiếng Nhật" v-model="form.languages">
              <label class="form-check-label">Tiếng Nhật</label>
            </div>
          </div>

          <button type="submit" class="btn btn-primary w-100">Đăng ký</button>
        </form>
      </div>

      <div class="col-md-6 mt-4 mt-md-0" v-if="isSubmitted">
        <h3 class="text-success">Thông tin đã đăng ký:</h3>
        <div class="p-3 border rounded bg-light">
          <p><strong>Họ tên:</strong> {{ info.name }}</p>
          <p><strong>Email:</strong> {{ info.email }}</p>
          <p><strong>Ngày sinh:</strong> {{ info.dob }}</p>
          <p><strong>Giới tính:</strong> {{ info.gender }}</p>
          <p><strong>Ngôn ngữ:</strong> {{ info.languages.join(', ') }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue';

const isSubmitted = ref(false);
const form = reactive({
  name: '', email: '', password: '', dob: '', gender: 'Nam', languages: []
});
const info = reactive({});

const register = () => {
  Object.assign(info, form);
  isSubmitted.value = true;
};
</script>