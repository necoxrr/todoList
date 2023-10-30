<script setup>
import { ref } from 'vue';
const newTodo = ref('')
const todos = ref([])
const finishTodo = ref([])
const visible = false

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

// 编辑代办事项
// 这一处有一个问题--就是直接在函数里改变visible的值是不可以的，现在所可以想的是直接用watch来监听visble
function edittodo() {






  // 弹出修改框

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
        <!-- 为什么在li中加（index,todo） in todos,{{ todo.titie }}中的文字显示不出来？？？ -->
        <li v-for="   todo in todos" :key="todo.id"><input type="checkbox" @click="deleteTodo(todo)"
            style="width: 40px;height: 20px;" /><span>{{ todo.title }}</span><button @click="edittodo()">编辑</button>
        </li>
      </ul>
    </div>

    <!-- 已经完成的区域 -->
    <div class="finish">
      <span
        style="width: 50px;height: 20px; background-color: cadetblue;font-family:'Times New Roman', Times, serif;">已完成</span>
      <ul class="todolist">
        <li v-for="finishdo in finishTodo" :key="finishdo.id" class="finishid"><span>{{ finishdo.title1 }}</span></li>
      </ul>
    </div>

    <!-- 弹出的修改事项框 -->
    <div style="width: 100px;height: 100px;background-color: bisque;" v-show="visible == true">

    </div>
  </div>
</template>
<style>
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
</style>
