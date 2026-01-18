<template>
  <div class="card">
    <div class="card-header">Viết bài mới</div>
    <div class="card-body">
      <form>
        <div class="mb-3">
          <label class="form-label">Tiêu đề bài viết</label>
          <input type="text" class="form-control">
        </div>
        <div class="mb-3">
          <label class="form-label">Hình ảnh (URL)</label>
          <input type="text" class="form-control" placeholder="https://...">
        </div>
        <div class="mb-3">
          <label class="form-label">Nội dung</label>
          <textarea class="form-control" rows="5"></textarea>
        </div>
        <button class="btn btn-primary">Đăng bài</button>
      </form>
    </div>
  </div>
</template>