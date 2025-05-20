<!-- src/components/Card.vue -->
<script setup>
// Принимаем пропсы
defineProps({
  borderColor: {
    type: String,
    default: '#ddd' // Цвет рамки по умолчанию
  }
})
</script>

<template>
  <div 
    class="card"
    :style="{ borderColor: borderColor }" 
  >
    <!-- Именованный слот для заголовка -->
    <header v-if="$slots.header" class="card-header">
      <slot name="header"></slot>
    </header>

    <!-- Слот по умолчанию -->
    <div class="card-content">
      <slot></slot>
    </div>

    <!-- Именованный слот для футера -->
    <footer v-if="$slots.footer" class="card-footer">
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<style scoped>
.card {
  border: 2px solid; /* Цвет будет задан через пропс */
  border-radius: 12px;
  padding: 20px;
  margin: 15px 0;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.card-header {
  font-size: 1.5em;
  margin-bottom: 15px;
  color: #2c3e50;
}

.card-footer {
  margin-top: 15px;
  padding-top: 15px;
  border-top: 1px solid #eee;
}
</style>