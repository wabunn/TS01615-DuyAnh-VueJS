<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col-sm-4">
        <h3 class="mb-3">{{ isEditing ? 'Cập nhật học sinh' : 'Thêm học sinh' }}</h3>
        
        <form @submit.prevent="submitForm">
          <div class="mb-3">
            <label for="name" class="form-label">Họ tên:</label>
            <input type="text" class="form-control" v-model="student.name" id="name" required placeholder="Nhập họ tên" />
          </div>

          <div class="mb-3">
            <label for="score" class="form-label">Điểm:</label>
            <input type="number" max="10" min="0" class="form-control" v-model="student.score" id="score" required placeholder="Nhập điểm" />
          </div>

          <div class="mb-3">
            <label for="dob" class="form-label">Ngày sinh:</label>
            <input type="date" class="form-control" v-model="student.dob" id="dob" required />
          </div>

          <button type="submit" class="btn" :class="isEditing ? 'btn-primary' : 'btn-success'">
            {{ isEditing ? 'Cập nhật' : 'Thêm' }}
          </button>
          
          <button v-if="isEditing" type="button" class="btn btn-secondary ms-2" @click="resetForm">Hủy</button>
        </form>
      </div>

      <div class="col-sm-8">
        <h3 class="mb-3">Danh sách học sinh</h3>
        <table class="table table-hover table-bordered">
          <thead class="table-light">
            <tr>
              <th>Họ và tên</th>
              <th>Điểm</th>
              <th>Ngày sinh</th>
              <th>Chức năng</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(stu, index) in students" :key="index">
              <td>{{ stu.name }}</td>
              <td>{{ stu.score }}</td>
              <td>{{ stu.dob }}</td>
              <td>
                <button class="btn btn-warning btn-sm me-2" @click="editStudent(index)">
                  Sửa
                </button>
                <button class="btn btn-danger btn-sm" @click="deleteStudent(index)">
                  Xóa
                </button>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const students = ref([
  { name: 'Nguyễn Chí Hùng', score: 8, dob: '2006-01-01' },
  { name: 'Phạm Thị Lan', score: 9, dob: '2006-05-15' }
]);

const student = ref({
  name: '',
  score: null,
  dob: ''
});

const isEditing = ref(false);
const editingIndex = ref(null);

function submitForm() {
  if (isEditing.value) {
    students.value[editingIndex.value] = { ...student.value };
    
    isEditing.value = false;
    editingIndex.value = null;
  } else {
    students.value.push({ ...student.value });
  }
  resetForm();
}

function editStudent(index) {
  student.value = { ...students.value[index] };
  isEditing.value = true;
  editingIndex.value = index;
}

function deleteStudent(index) {
  if (confirm('Bạn có chắc chắn muốn xóa học sinh này không?')) {
    students.value.splice(index, 1);
  }
}

function resetForm() {
  student.value = {
    name: '',
    score: null,
    dob: ''
  };
  isEditing.value = false;
  editingIndex.value = null;
}
</script>