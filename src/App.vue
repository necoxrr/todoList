<script setup>
import edit from './components/EditComponent.vue'
import { createApp } from 'vue'
import { ref } from 'vue';
const newTodo = ref('')
const todos = ref([])
const finishTodo = ref([])
// 全局添加组件
const app = createApp({})
app.component(
  'edit'
)
// 弹框显示
const show = ref(false)
// 添加新的事项的事件
let next = 4
function addNewTodo() {
  todos.value.push({
    id: next++,
    title: newTodo.value
  })
  newTodo.value = ''
}

// 代办事件的完成
function deleteTodo(todo) {
  todos.value.splice(todo, 1)
  finishTodo.value.push({
    id: next++,
    title1: todo.title
  })
}
// 已经完成事情的删除
function deleteFinish(finishdo) {
  finishTodo.value.splice(finishdo, 1)

}
// 弹框的产生
function editTitle() {
  show.value = true
}
function real(val) {
  console.log(val)

}
</script>

<template>
  <div class="todo">

    <!-- todolist输入和展示完成事项的区块 -->
    <div>
      <input id="new-todo" placeholder="请输入待办事项" v-model="newTodo" :key="index" />
      <button @click="addNewTodo">添加</button>
      <br />
      <ul class="todolist">
        <li v-for="   todo in todos" :key="todo.id"><input type="checkbox" @click="deleteTodo(todo)"
            style="width: 40px;height: 20px;" /><span>{{ todo.title }}</span><button @click="editTitle">编辑</button>
        </li>
      </ul>
    </div>

    <!-- 已经完成的区域 -->
    <div class="finish">
      <span
        style="width: 50px;height: 20px; background-color: cadetblue;font-family:'Times New Roman', Times, serif;">已完成</span>
      <ul class="todolist">
        <li v-for="finishdo in finishTodo" :key="finishdo.id" class="finishid"><span>{{ finishdo.title1 }}</span>
          <button @click="deleteFinish(finishdo)">删除</button>
        </li>
      </ul>
    </div>

    <!-- 编辑框 -->
    <edit class="dump" v-model:show="show" @out="out"></edit>

  </div>
</template>
<style scoped>
/* 去标签黑点的样式 */
.todolist {
  list-style-type: none;
}

/* 总的todolist的样式 */
.todo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: antiquewhite;
}

/* 完成板块的显示 */
.finish {
  background-color: aquamarine;
}

/* 完成事项的设计 */
.finishid {
  background-color: gray;
}

/* 弹出编辑框的样式 */
.dump {
  position: fixed;
  z-index: 999;
  top: 20%;
  left: 60%;
  width: 300px;
  height: 700px;

}
</style>
