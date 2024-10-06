<script setup>
import { ref } from "vue";
//modelo 
const header = ref('App lista de Compras');
// ---Items---
const items = ref([
    {id:'0', label: '10 bolillos'}, 
    {id:'1', label: '1 lata de volt'}, 
    {id:'2', label: '1 bote de café'},
    {id:'3', label: '10 chetos'}
]);
//Item-Method
const saveItem = () => {
    //Agregamos otro item
    items.value.push({id: items.value.length + 1, label: newItem.value});
    //queda vacia la caja de texto
    newItem.value = '';
    
}

const newItem = ref(''); 
const newItemHighPriority = ref(false);

//metodo para crear el hipervinculo
const hipervinculo = () => {
    return newItem.value === '' ? 'https://www.google.com' :
    'https://' + newItem.value;
}

</script>


<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
</h1>

<!-- Hipervinculo -->
<a v-bind:href="hipervinculo()" target="_blank">
  {{ newItem == '' ? 'link' : newItem }}
</a>

<!-- Agrupando en un div las entradas -->
<form class="add-item form" v-on:submit.prevent="saveItem">
    
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
    <!-- Lista de items -->
    <ul>
        <li v-for="({id,label}, i) in items" :key="id"> {{ i+1 }} {{i%2==0?'🔥':'🛍️'}} {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
