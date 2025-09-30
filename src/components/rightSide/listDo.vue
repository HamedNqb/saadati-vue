<script setup>
defineProps({
  items: {
    type: Array,
    default: () => []
  }
})
</script>

<template>
  <div class="list">
    <h2>لیست</h2>
    <ul>
      <li v-if="items.length === 0">آیتمی وجود ندارد</li>
      <li v-for="it in items" :key="it._id" class="item">
        <div class="meta">
          <strong>{{ it.date || '—' }}</strong>
        </div>
        <div class="tozih">{{ it.tozih || '—' }}</div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.list {
  border: 1px solid #aaa;
  padding: 12px;
  border-radius: 6px;
  background: #fff;
  max-height: 60vh;
  overflow: auto;
}
.list ul { margin: 0; padding: 0; list-style: none; }
.item { padding: 8px; border-bottom: 1px dashed #ddd; }
.item:last-child { border-bottom: none; }
.meta { margin-bottom: 6px; }
.tozih { white-space: pre-wrap; color: #333; }
</style>
