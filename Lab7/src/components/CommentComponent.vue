<template>
  <div class="card p-4">
    <h2 class="text-center">Bình luận bài viết</h2>

    <div class="card mb-3">
      <img src="../assets/img2.jpg" class="card-img-top" alt="Hình ảnh">
      <div class="card-body">
        <h3 class="card-title">8 loại rau củ quả giàu canxi</h3>
        <p class="card-text">
          Canxi là khoáng chất cần thiết đối với cơ thể người. Có nhiều cách để bổ sung canxi,
          trong đó bổ sung qua đường ăn uống là cách tốt nhất.
        </p>
      </div>
    </div>

    <form @submit.prevent="submitComment">
      <div class="mb-3">
        <textarea class="form-control" rows="3" v-model="commentText" placeholder="Nhập bình luận của bạn"></textarea>
      </div>
      <button type="submit" class="btn btn-success">Gửi bình luận</button>
    </form>

    <div v-if="comments.length" class="mt-4">
      <h5>Danh sách các bình luận:</h5>
      <ul class="list-group">
        <li class="list-group-item" v-for="(comment, index) in comments" :key="index">
          <strong>{{ comment.name }}:</strong> {{ comment.text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps(['username']);

const commentText = ref('');
const comments = ref([]);

function submitComment() {
  if (commentText.value) {
    comments.value.push({
      name: props.username,
      text: commentText.value
    });
    commentText.value = '';
  }
}
</script>