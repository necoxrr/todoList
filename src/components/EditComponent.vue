<script setup>
import { ref, defineExpose, reactive } from 'vue';
const visible = ref(false)
const open = () => {
  visible.value = true
}

defineExpose({
  open,
  changeTitle
})
const change = () => {
  visible.value = false
}
const todoForm = reactive({
  new: '',
})
const changeTitle = (row) => {

}
</script>
<template>
  <!-- 编辑所出现的弹框-->

  <el-dialog title="事项" v-model="visible" center append-to-body>
    <el-form :model="todoForm">
      <el-form-item label="代办事项：">
        <el-input v-model="todoForm.new"></el-input>
      </el-form-item>
    </el-form>
    <template v-slot:footer>
      <el-button @click="change">确认</el-button>
    </template>
  </el-dialog>
</template>

