<template>
    <button 
      @mouseenter="hover = true"
      @mouseleave="hover = false">
      <slot name="icon" :hover="hover">⭐</slot>
      <slot></slot> 
  </button>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  const hover = ref(false);
  </script>
  
  <style scoped>
  .content{
  text-align: center;
}
button{
  width: auto;
  margin: 0px auto;
  font-size: 2rem;
}
  </style>