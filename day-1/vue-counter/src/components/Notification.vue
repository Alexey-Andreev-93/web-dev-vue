<script setup>
defineProps({
  show: Boolean
})
</script>

<template>
  <div v-if="show" class="notification">
    ⚠️ Счётчик превысил 20!
  </div>
</template>

<style scoped>
.notification {
  padding: 10px;
  margin-top: 15px;
  background: #ff4757;
  color: white;
  border-radius: 4px;
  animation: fadeIn 0.3s;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}
</style>