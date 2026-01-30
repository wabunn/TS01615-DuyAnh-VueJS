<template>
  <div class="container-fluid py-4">
    <h1 class="text-center text-primary mb-4">FPT Polytechnic - Lab 6 VueJS</h1>
    
    <ul class="nav nav-tabs mb-4" id="myTab" role="tablist">
      <li class="nav-item" role="presentation">
        <button class="nav-link" :class="{ active: currentTab === 1 }" @click="currentTab = 1">Bài 1</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" :class="{ active: currentTab === 2 }" @click="currentTab = 2">Bài 2</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" :class="{ active: currentTab === 3 }" @click="currentTab = 3">Bài 3</button>
      </li>
      <li class="nav-item" role="presentation">
        <button class="nav-link" :class="{ active: currentTab === 4 }" @click="currentTab = 4">Bài 4</button>
      </li>
    </ul>

    <div class="tab-content bg-white p-3">
      <div v-if="currentTab === 1">
        <h2 class="text-danger mb-3">Bài 1: Xếp loại học sinh</h2>
        <Bai1 />
      </div>

      <div v-if="currentTab === 2">
        <h2 class="text-danger mb-3">Bài 2: Xác định mùa</h2>
        <Bai2 />
      </div>

      <div v-if="currentTab === 3">
        <Bai3 />
      </div>

      <div v-if="currentTab === 4">
        <Bai4 />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

import Bai1 from './components/Bai1.vue';
import Bai2 from './components/Bai2.vue';
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';

const currentTab = ref(1);
</script>

<style>
body {
  background-color: #f8f9fa;
}
.nav-link {
  cursor: pointer;
  font-weight: 500;
}
</style>