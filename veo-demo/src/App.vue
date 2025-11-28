<script setup>
import { ref } from 'vue'

const title = ref('本周待办事项')
const newItem = ref('') // 输入框绑定的内容
const todoList = ref([  // 待办列表数据
  { id: 1, text: '完成 Vue 作业' },
  { id: 2, text: '复习 HTML 基础' }
])

function add() {
  if (newItem.value.trim() === '') {
    alert('请输入内容！')
    return
  }
  todoList.value.push({
    id: Date.now(), 
    text: newItem.value
  })
  newItem.value = ''
}

function clearAll() {
  todoList.value= []
}

function remove(id) {
  todoList.value = todoList.value.filter(item => item.id != id)
}

</script>

<template>
  <div class="app-wrapper">
    <h1>{{ title }}</h1>

    <div class="input-group">
      <input 
        class="input" 
        type="text" 
        v-model="newItem" 
        placeholder="请输入待办事项..."
      />
      <button class="in-btn" @click="add">添加</button>
    </div>

    <div class="container">
      <ul v-if="todoList.length > 0">
        <li v-for="item in todoList" :key="item.id">
          <span>{{ item.text }}</span>
          <button class="del-btn" @click="remove(item.id)">删除</button>
        </li>
      </ul>
    </div>
    <button class="delall" @click="clearAll">清空所有</button>
  </div>
</template>

<style scoped>

.app-wrapper {
  width: 600px;
  margin: 0 auto;
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  background-color: rgb(224, 220, 220);
}

h1 {
  font-weight: bold;
  color: rgb(24, 24, 24);
  margin-bottom: 20px;
}

.input-group {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.input {
  height: 30px;
  width: 400px;
  border: 1px solid blue;
  border-radius: 10px;
  padding: 5px;
  font-size: 16px;
}

.in-btn {
  background-color: skyblue;
  padding: 10px;
  color: black;
  border: none;
  border-radius: 10px;
  margin-left: 10px;
  cursor: pointer;
}

.container {
  margin-bottom: 10px;
  text-align: left;
}

ul {
  list-style: none;
  padding: 10px;
}

li {
  background-color: honeydew;
  border-radius: 10px;
  padding: 10px;
  margin: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.del-btn {
  background-color: red;
  padding: 10px;
  color: white;
  border: none;
  border-radius: 10px;
  cursor: pointer;
}

.delall {
  background-color: #160302;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.5s;
}

.delall:hover {
  background-color: white;
  color: red;
}

</style>