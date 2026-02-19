<template>
  <div>
    <h2>Trang thông tin cá nhân</h2>
    <nav>
      <router-link :to="{ name: 'UserProfileInfo' }">Thông tin cơ bản</router-link> | 
      <router-link :to="{ name: 'UserProfileSettings' }">Cài đặt</router-link>
    </nav>
    <hr>
    <router-view></router-view>
  </div>
</template>