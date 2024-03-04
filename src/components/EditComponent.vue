<script setup>
import { defineProps, ref, defineExpose, reactive, watch } from 'vue';
const visible = ref(false)
const props = defineProps(['editTodo', 'setBack']);
const open = () => {
  visible.value = true
}
defineExpose({
  open,
})
const change = () => {
  visible.value = false
}
const todoForm = reactive({
  new: '',
})
watch(() => props.editTodo, (newValue) => {
  todoForm.new.value = newValue.title;
});
console.log('help', props);
const submit = () => {
  props.setBack({
    ...props.editTodo,
    title: todoForm.new.value,
  });
};

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
      <el-button @click="change">取消</el-button>
      <el-button @click="submit">提交</el-button>
    </template>
  </el-dialog>
</template>
