<script setup>
import { ref } from 'vue'
import CounterButton from './components/CounterButton.vue';

const count = ref(0)

const increment = () => {
  console.log(count.value++)
}
const decrement = () => count.value--
const reset = () => count.value = 0
const addTen = () => count.value += 10
const removeFive = () => count.value -= 5
const multiplyTwo = () => count.value ** 2

</script>

<template>
  <div>
    <h1
     :class="{'red-text' : count >= 10}"
    >
      Счётчик: {{ count }}
    </h1>

    <div class="buttons">
      <CounterButton
        :action="() => increment"
        label="+1"
        color="#42b983"
      />

      <CounterButton
        :action="() => decrement"
        label="-1"
        color="#ff4757"
      />

      <CounterButton
        :action="() => addTen"
        label="+10"
        color="#2c3e50"
      />

      <CounterButton
        :action="() => removeFive"
        label="-5"
        color="#e84118"
      />

      <CounterButton
        :action="() => reset"
        label="Сброс"
        color="green"
      />

      <CounterButton
        :action="multiplyTwo"
        label="* 2"
        color="violet"
      />
    </div>
  </div>
</template>

<style>
  .red-text {
    color: #e84118;
    transition: color 0.3s;
  }

  .container {
    text-align: center;
    margin-top: 2rem;
  }

  .buttons {
    margin-top: 1rem;
  }
</style>