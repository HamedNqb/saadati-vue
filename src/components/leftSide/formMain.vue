<script setup>
import { ref } from 'vue'

const date = ref('')
const tozih = ref('')

const emit = defineEmits(['send-item'])

const submitForm = (e) => {
  e.preventDefault()
  emit('send-item', { date: date.value.trim(), tozih: tozih.value.trim() })
  date.value = ''
  tozih.value = ''
}
</script>

<template>
  <form class="form" @submit="submitForm">
    <label for="date">تاریخ (رشته):</label>
    <input v-model="date" type="text" id="date" class="input" placeholder="مثال: 2025-09-30">

    <label for="tozih">توضیح:</label>
    <textarea v-model="tozih" id="tozih" class="textarea" rows="4" placeholder="توضیحات..."></textarea>

    <button class="btn" type="submit">ارسال</button>
  </form>
</template>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  padding: 16px;
  border: 2px solid #444;
  border-radius: 8px;
  background: #fff;
}
.input, .textarea {
  padding: 8px;
  border: 1px solid #aaa;
  border-radius: 4px;
  font-size: 14px;
}
.btn {
  padding: 8px 12px;
  background: #2d89ef;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  align-self: flex-start;
}
.btn:hover { background: #1a5dbb; }
</style>
