<script setup>
import { computed, ref } from 'vue'
import CounterButton from './components/CounterButton.vue'
import Notification from './components/Notification.vue'

const count = ref(0)
const showWarning = computed(() => count.value >= 20) 

// Функции для разных действий
const increment = () => count.value++
const decrement = () => count.value--
const reset = () => count.value = 0
const addTen = () => count.value += 10
const multiplyTwo = () => count.value -= 5
</script>

<template>
  <div class="container">
    <h1 :class="{ 'red-text': count >= 10}">
      Счётчик: {{ count }}
    </h1>

    <!-- Группа кнопок -->
    <div class="buttons">
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

    <Notification :show="showWarning"/>
  </div>
</template>

<style>
.red-text {
  color: #e84118;
  transition: color 0.3s;
}

.blue-text {
  color: blue;
}

.container {
  text-align: center;
  margin-top: 2rem;
}

.buttons {
  margin-top: 1rem;
}
</style>