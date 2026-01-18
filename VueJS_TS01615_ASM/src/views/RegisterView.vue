<template>
  <div class="row justify-content-center">
    <div class="col-md-6">
      <div class="card shadow">
        <div class="card-header bg-success text-white text-center">
          <h4>Đăng Ký Tài Khoản</h4>
        </div>
        <div class="card-body p-4">
          <form>
            <div class="row">
              <div class="col-md-6 mb-3">
                <label class="form-label">Họ tên</label>
                <input type="text" class="form-control">
              </div>
              <div class="col-md-6 mb-3">
                <label class="form-label">Tên đăng nhập</label>
                <input type="text" class="form-control">
              </div>
            </div>
            <div class="mb-3">
              <label class="form-label">Email</label>
              <input type="email" class="form-control">
            </div>
            <div class="mb-3">
              <label class="form-label">Mật khẩu</label>
              <input type="password" class="form-control">
            </div>
            <button class="btn btn-success w-100">Đăng ký</button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>