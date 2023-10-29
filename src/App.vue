<script setup>
import { ref } from 'vue';
const newTodo = ref('')
const todos = ref([])
// 添加新的事项的事件
let next = 4
function addNewTodo() {
  todos.value.push({
    id: next++,
    title: newTodo.value
  })
  newTodo.value = ''

}
function deleteTodo(index) {
  todos.value.splice(index, 1)
}
// 完成待办事项后删除
// function finish() {
//   todos.value.splice()
// }
</script>
<template>
  <input id="new-todo" placeholder="请输入待办事项" v-model="newTodo" :key="index" />
  <button @click="addNewTodo">添加</button>
  <br />
  <ul class="todolist">
    <!-- 为什么在li中加（index,todo） in todos,{{ todo.titie }}中的文字显示不出来？？？ -->
    <li v-for="  (index, todo) in todos" :key="todo.id"><input type="checkbox" @click="deleteTodo(index)"
        style="width: 40px;height: 20px;" /><span>{{ todo.title }}</span>
    </li>
  </ul>
</template>
<style>
.todolist {
  list-style-type: none;
}
</style>
