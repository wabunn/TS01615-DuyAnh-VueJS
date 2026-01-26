<template>
  <div class="container mt-4">
    <h1 class="text-primary text-center mb-5">LAB 5_TS01615_ĐỖ DUY ANH</h1>

    <Bai4 />
    </div>
</template>

<script setup>
import Bai1 from './components/Bai1.vue';
import Bai2 from './components/Bai2.vue';
import Bai3 from './components/Bai3.vue';
import Bai4 from './components/Bai4.vue';
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 20px;
}

.container { padding: 15px; }
.text-center { text-align: center; }
.mb-3 { margin-bottom: 1rem; }
.mb-5 { margin-bottom: 3rem; }
.form-control {
    width: 100%;
    padding: 8px;
    margin-top: 5px;
    box-sizing: border-box; 
    border: 1px solid #ccc;
    border-radius: 4px;
}
.btn {
    padding: 8px 16px;
    cursor: pointer;
    border: none;
    border-radius: 4px;
}
.btn-dark { background-color: #333; color: white; }
.bg-dark { background-color: #333; }
.text-white { color: white; }
.p-3 { padding: 1rem; }
.p-5 { padding: 3rem; }
.rounded { border-radius: 0.25rem; }
</style>