<!-- App.vue -->
<template>
  <div class="parent-container">
    <h1>Kata-kata Mutiara</h1>
    
    <Child1 
      @childEvent="updateMessage" 
      @child1ButtonClicked="handleChild1ButtonClick"
      :child2ButtonState="child2ButtonState"
    >
      <template #default>

      </template>
    </Child1>
    
    <Child2 
      @childEvent="updateMessage" 
      @child2ButtonClicked="handleChild2ButtonClick"
      :child1ButtonState="child1ButtonState"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Child1 from './components/Child1.vue'
import Child2 from './components/Child2.vue'

const message = ref('No message yet.')
const child1ButtonState = ref(false)
const child2ButtonState = ref(false)

const updateMessage = (msg) => {
  message.value = msg
}

const handleChild1ButtonClick = () => {
  child2ButtonState.value = !child2ButtonState.value
}

const handleChild2ButtonClick = () => {
  child1ButtonState.value = !child1ButtonState.value
}
</script>

<style scoped>
.parent-container {
  text-align: center;
  font-family: Arial, sans-serif;
  margin: 20px;
}

p {
  font-size: 16px;
  margin-bottom: 20px;
}

.slot-content {
  background-color: #f0f0f0;
  padding: 10px;
  border-radius: 5px;
  display: inline-block;
}
</style>
