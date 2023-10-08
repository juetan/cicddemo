<script setup lang="ts">
import { onMounted, ref } from 'vue';

const message = ref('hello world');

onMounted(async () => {
  try {
    const res = await fetch('/api/message');
    const data = await res.text();
    message.value = data;
  } catch {
    message.value = '获取失败';
  }
});
</script>

<template>
  <div>
    {{ message }}
  </div>
</template>

<style scoped>
</style>
