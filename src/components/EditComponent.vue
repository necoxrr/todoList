<script setup>
import { ref } from 'vue';
const dialogVisible = ref(false)
</script>
 <!-- 弹出的修改事项框 -->
<template>
  <!-- 编辑所出现的弹框-->
  <el-dialog title="事项" v-model:visible="dialogVisible" center append-to-body>
    <el-form :model="todoForm">
      <el-form-item label="代办事项：">
        <el-input v-model="todoForm.reverseTodo"></el-input>
      </el-form-item>
    </el-form>
    <template v-slot:footer>
      <el-button @click="closeDialog">确认</el-button>
    </template>


  </el-dialog>
</template>

