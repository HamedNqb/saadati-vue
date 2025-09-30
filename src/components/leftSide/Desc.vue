<script setup>
defineProps({
  item: {
    type: Object,
    default: null
  }
})
</script>

<template>
  <div class="desc">
    <h3>آخرین مقدار ثبت‌شده</h3>
    <div v-if="item && (item.date || item.tozih)">
      <p><strong>تاریخ:</strong> {{ item.date || '—' }}</p>
      <p><strong>توضیح:</strong></p>
      <p class="tozih">{{ item.tozih || '—' }}</p>
    </div>
    <p v-else>هنوز چیزی ثبت نشده</p>
  </div>
</template>

<style scoped>
.desc {
  border: 1px solid #999;
  border-radius: 6px;
  padding: 12px;
  background: #f7f7f7;
}
.tozih {
  white-space: pre-wrap;
  margin: 8px 0 0;
}
</style>
