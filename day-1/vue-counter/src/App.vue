<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>

<template>
  <div>
    <h1 :class="{'red-text' : count >= 10}">Счётчик: {{ count }}</h1>
    <button @click="count++">+1</button>
    <button @click="count--">-1</button>
    <button @click="count += 10">+10</button>
    <button @click="count = 0">Сброс</button>
  </div>
</template>