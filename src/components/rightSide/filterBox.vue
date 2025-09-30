<script setup>
import { ref, watch } from 'vue'

const emit = defineEmits(['update-filter'])
const props = defineProps({
  value: {
    type: String,
    default: ''
  }
})

const local = ref(props.value)

watch(local, (newVal) => {
  emit('update-filter', newVal)
})
</script>

<template>
  <div class="filter">
    <label>فیلتر بر اساس تاریخ:</label>
    <input v-model="local" type="text" class="input" placeholder="مثال: 2025-09-30 یا بخشی از تاریخ">
    <small>برای حذف فیلتر، فیلد را خالی کنید.</small>
  </div>
</template>

<style scoped>
.filter {
  display: flex;
  flex-direction: column;
  gap: 6px;
}
.input {
  padding: 8px;
  border: 1px solid #aaa;
  border-radius: 4px;
}
</style>
