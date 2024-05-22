<!-- components/Child1.vue -->
<template>
    <div class="child-container">
      <h2>Pertama</h2>
      <slot></slot>
      <button @click="toggleDescription1">{{ showDescription1 ? 'Hide' : 'Show' }} Description</button>
      <p v-if="showDescription1">"Ketika hati dipenuhi syukur, pikiran menjadi tenang dan jiwa terasa damai.".</p>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  const emit = defineEmits(['childEvent', 'child1ButtonClicked'])
  const props = defineProps({
    child2ButtonState: Boolean
  })
  
  const showDescription1 = ref(false)
  
  const toggleDescription1 = () => {
    showDescription1.value = !showDescription1.value
  }
  
  const child1ButtonClick = () => {
    emit('child1ButtonClicked')
  }
  </script>
  
  <style scoped>
  .child-container {
    border: 1px solid #ccc;
    padding: 20px;
    border-radius: 10px;
    margin: 10px 0;
  }
  
  h2 {
    color: #3eaf7c;
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
  