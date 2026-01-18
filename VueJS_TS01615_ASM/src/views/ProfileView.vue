<template>
  <div class="row">
    <div class="col-md-4 mb-3">
      <div class="card text-center">
        <div class="card-body">
          <img src="https://placehold.co/150" class="rounded-circle mb-3" alt="Avatar">
          <h4>Tên Người Dùng</h4>
          <p class="text-muted">user@example.com</p>
        </div>
      </div>
    </div>
    <div class="col-md-8">
      <div class="card">
        <div class="card-header">Cập nhật thông tin</div>
        <div class="card-body">
          <form>
            <div class="mb-3">
              <label class="form-label">Họ và tên</label>
              <input type="text" class="form-control" value="Tên Người Dùng">
            </div>
            <div class="mb-3">
              <label class="form-label">Email</label>
              <input type="email" class="form-control" value="user@example.com" disabled>
            </div>
             <div class="mb-3">
              <label class="form-label">Mật khẩu mới</label>
              <input type="password" class="form-control">
            </div>
             <div class="mb-3">
              <label class="form-label">URL Ảnh đại diện</label>
              <input type="text" class="form-control">
            </div>
            <button class="btn btn-primary">Lưu thay đổi</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>