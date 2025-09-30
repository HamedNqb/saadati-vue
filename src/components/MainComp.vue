<script setup>
import { ref } from 'vue'
import MainLeft from './leftSide/mainLeft.vue'
import MainRight from './rightSide/mainRight.vue'

const items = ref([])


const handleNewItem = (item) => {

  const withMeta = {
    ...item,
    _id: Date.now()
  }
  items.value.unshift(withMeta)
}
</script>

<template>
  <main class="main">
    <MainLeft @send-item="handleNewItem" />
    <MainRight :items="items" />
  </main>
</template>

<style scoped>
@font-face {
  font-family: 'IRANYekan';
  src: url('@/IRANYekan.woff2') format('woff2');
  font-weight: normal;
  font-style: normal;
  font-display: swap;
}

.main {
  display: flex;
  gap: 20px;
  height: 100vh;
  padding: 20px;
  background: antiquewhite;
  box-sizing: border-box;
  font-family: 'IRANYekan';

}
</style>
