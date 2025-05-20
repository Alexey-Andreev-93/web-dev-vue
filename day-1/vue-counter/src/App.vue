<script setup>
import { computed, ref } from 'vue'
import CounterButton from './components/CounterButton.vue'
import Notification from './components/Notification.vue'
import Card from './components/Card.vue'

const count = ref(0)
const history = ref([]) 
const showWarning = computed(() => count.value >= 20) 

// Добавляем значение в историю
const addToHistory = (newValue) => {
  history.value.push(newValue)
  
  // Ограничиваем историю 5 последними значениями
  if (history.value.length > 5) {
    history.value.shift()
  }

}

const borderColor = computed(() => {
  return count.value >= 10 ? '#ff4757' : '#42b983'
})

// Функции для разных действий
const increment = () => {
  count.value++
  addToHistory(count.value)
}
const decrement = () => {
  count.value--
  addToHistory(count.value)
}
const reset = () => {
  count.value = 0
  addToHistory(count.value)
}
const addTen = () => {
  count.value += 10
  addToHistory(count.value)
}
const multiplyTwo = () => {
  count.value -= 5
  addToHistory(count.value)
}
</script>

<template>
  <Card :border-color="borderColor">
    <!-- Именованный слот "header" -->
    <template #header>
      <h2>Умный счётчик</h2>
      <p>Текущее значение: {{ count }}</p>
    </template>

    <!-- Слот по умолчанию -->
    <div class="controls">
      <CounterButton 
        :action="increment" 
        label="+1" 
        color="#42b983"

      />
      
      <CounterButton 
        :action="addTen" 
        label="+10" 
        color="#2c3e50"
        
      />
      
      <CounterButton 
        :action="decrement" 
        label="-1" 
        color="#ff4757"

      />
      
      <CounterButton 
        :action="reset" 
        label="Сброс" 
        color="#e84118"

      />

      <CounterButton
        :action="multiplyTwo"
        label="-5"
        color="eb0c0c"
      />
    </div>

    <!-- Именованный слот "footer" -->
    <template #footer>
      <div v-if="history.length > 0" class="history">
        <h3>История изменений:</h3>
        <ul>
          <li 
            v-for="(item, index) in history" 
            :key="index"
            class="history-item"
          >
            Шаг {{ index + 1 }}: {{ item }}
          </li>
        </ul>
      </div>
    </template>
  </Card>

  <Notification :show="showWarning"/>
</template>

<style>
.controls {
  display: flex;
  gap: 10px;
  margin: 15px 0;
}

.history {
  margin-top: 20px;
}

.history-item {
  padding: 5px;
  transition: background 0.3s;
}

.history-item:hover {
  background: #f8f9fa;
}
</style>

    <!-- Группа кнопок -->
