<script setup>
import { ref } from 'vue'
import FormMain from './formMain.vue'
import Desc from './desc.vue'


const emit = defineEmits(['send-item'])

const latestItem = ref(null)


const handleSend = (payload) => {

  latestItem.value = payload

  emit('send-item', payload)
}
</script>

<template>
  <div class="left">
    <FormMain @send-item="handleSend" />
    <Desc :item="latestItem" />
  </div>
</template>

<style scoped>
.left {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 16px;
  border: 2px solid #666;
  border-radius: 8px;
  background: #fafafa;
  width: 40%;
}
</style>
