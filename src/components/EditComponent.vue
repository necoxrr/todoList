<script setup>
import { ref, defineProps } from 'vue';
const props = defineProps({
  visible: Boolean
});
const visiblel = ref(props.visible);
</script>
 <!-- 弹出的修改事项框 -->
<template>
  <!-- 编辑所出现的弹框-->

  <el-dialog title="事项" v-model="visiblel" center append-to-body>
    <el-form>
      <el-form-item label="代办事项：">
        <el-input></el-input>
      </el-form-item>
    </el-form>
    <template v-slot:footer>
      <el-button @click="$emit('close')">确认</el-button>
    </template>
  </el-dialog>
</template>

