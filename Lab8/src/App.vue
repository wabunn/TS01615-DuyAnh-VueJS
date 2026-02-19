<template>
  <div id="app">
    <nav>
      <router-link :to="{ name: 'Home' }">Trang chủ</router-link> | 
      <router-link :to="{ name: 'BlogList' }">Danh sách Blog</router-link> | 
      <router-link :to="{ name: 'UserProfile' }">Profile</router-link> | 
      <router-link to="/me">Profile (me)</router-link> | 
      <router-link :to="{ name: 'Dashboard' }">Dashboard</router-link> | 
      <router-link :to="{ name: 'Login' }">Đăng nhập</router-link>
    </nav>
    <hr>
    
    <router-view></router-view>
  </div>
</template>

<style>
nav {
  margin-bottom: 20px;
  background-color: #f5f5f5;
  padding: 15px;
}
nav a {
  margin-right: 10px;
  text-decoration: none;
  font-weight: bold;
  color: #333;
}
nav a.router-link-active {
  color: #42b983;
}
</style>