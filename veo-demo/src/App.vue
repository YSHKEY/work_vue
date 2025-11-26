<script setup>
// 1. 这里写 JavaScript (逻辑)
import { ref } from 'vue'

// 定义数据
const title = ref('我的第一个 Vue 工程化作业')
const count = ref(0)

// 定义函数
function add() {
  count.value++
}
</script>

<template>
  <!-- 2. 这里写 HTML (结构) -->
  <div class="container">
    <h1>{{ title }}</h1>
    <p>当前计数：{{ count }}</p>
    <button @click="add">点击加 1</button>
  </div>
</template>

<style scoped>
/* 3. 这里写 CSS (样式) */
.container {
  text-align: center;
  margin-top: 50px;
  font-family: sans-serif;
}

h1 {
  color: #42b883;
}

button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}
</style>