<script setup>
import { ref, computed } from 'vue'
import FilterBox from './filterBox.vue'
import ListDo from './listDo.vue'

const props = defineProps({
  items: {
    type: Array,
    default: () => []
  }
})

const filterDate = ref('')

const filteredItems = computed(() => {
  const f = filterDate.value.trim()
  if (!f) return props.items
  return props.items.filter(it => (it.date || '').includes(f))
})

const handleUpdateFilter = (val) => {
  filterDate.value = val
}
</script>

<template>
  <div class="right">
    <FilterBox :value="filterDate" @update-filter="handleUpdateFilter" />
    <ListDo :items="filteredItems" />
  </div>
</template>

<style scoped>
.right {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 16px;
  border: 2px solid #666;
  border-radius: 8px;
  background: #f9f9f9;
  flex: 1;
  width: 40%;
}
.summary {
  font-size: 14px;
  color: #333;
  margin-bottom: 6px;
}
</style>
