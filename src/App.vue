<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
const items = ref([
    {id:'0', label: '10 bolillos'}, 
    {id:'1', label: '1 lata de volt'}, 
    {id:'2', label: '1 bote de café'},
    {id:'3', label: '10 chetos'}
]);
const newItem = ref(''); 
const newItemHighPriority = ref(false);
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>

<!-- Agrupando en un div las entradas -->
<form v-on:submit.prevent="items.push({ id: items.length + 1, label: newItem })" class="add-item fomr">
    
    <!-- entrada de texto -->
    <input
      v-model.trim="newItem"
      type="text"
      placeholder="Add Item">
    
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      Alta prioridad
    </label>

    <!-- Boton -->
    <button class="btn btn-primary"> Guardar </button>
  
</form>
    
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🔥':'🛍️'}} {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
