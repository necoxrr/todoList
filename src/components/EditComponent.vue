<script setup>
import { defineProps } from 'vue';
defineProps(['show'])
// const emit = defineEmits({
//   show.value = false

// })


</script>
 <!-- 弹出的修改事项框 -->
<template>
  <div style="width: 100px;height: 100px;background-color: bisque;" v-if="show">
    <button @click="out1"></button>
  </div>
</template>

