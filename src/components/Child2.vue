<!-- components/Child2.vue -->
<template>
    <div class="nested-container">
      <h2>Kedua</h2>
      <button @click="toggleDescription2">{{ showDescription2 ? 'Hide' : 'Show' }} Description</button>
      <p v-if="showDescription2">"Kalau belum tenang itu berarti anda kurang bersyukur,plus ngasih tugas kebanyakan pada adik tingkat:3".</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  const emit = defineEmits(['childEvent', 'child2ButtonClicked'])
  const props = defineProps({
    child1ButtonState: Boolean
  })
  
  const showDescription2 = ref(false)
  
  const toggleDescription2 = () => {
    showDescription2.value = !showDescription2.value
  }
  
  const child2ButtonClick = () => {
    emit('child2ButtonClicked')
  }
  </script>
  
  <style scoped>
  .nested-container {
    border: 1px dashed #3eaf7c;
    padding: 15px;
    border-radius: 10px;
    margin-top: 10px;
  }
  
  h2 {
    color: #42b983;
  }
  
  button {
    padding: 10px 20px;
    font-size: 14px;
    cursor: pointer;
    background-color: #42b983;
    border: none;
    color: white;
    border-radius: 5px;
    transition: background-color 0.3s ease;
    margin-bottom: 10px;
  }
  
  button:hover {
    background-color: #3eaf7c;
  }
  </style>
  