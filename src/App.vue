<script setup>
import { ref, computed } from "vue";
//modelo 
const header = ref('App lista de Compras');
// ---Items---
const items = ref([
    {id:'0', label: '10 bolillos',purchased: true, priority: true}, 
    {id:'1', label: '1 lata de volt',purchased: true, priority: true}, 
    {id:'2', label: '1 bote de café',purchased: false, priority: false},
    {id:'3', label: '10 chetos',purchased: false, priority: false}
]);
//Item-Method
const saveItem = () => {
    //Metodo para agregar otro item a la lista
    items.value.push({
      id: items.value.length + 1, 
      label: newItem.value,
      highPriority: newItemHighPriority.value
    });
    //reiniciando la entrada de texto
    newItem.value = '';
    newItemHighPriority.value = false;
    
};
const doEdit = (edit)=>{
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};

const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(false);

// Alternando estado de compra del item
const togglePurchased = (item) => {
  item.purchased = !item.purchased;
};

// Creando una propiedad computada
const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
});

// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse();
});

//metodo para crear el hipervinculo
/*const hipervinculo = () => {
    return newItem.value === '' ? 'https://www.google.com' :
    'https://' + newItem.value;
}*/
</script>

<template>
<div class="header">
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>
  <button v-if="editing" class="btn" @click="doEdit(false)">CANCELAR</button>
  <button v-else class="btn btn-primary" @click="doEdit(true)">AGREGAR ARTICULO</button>
</div>

<!-- Hipervinculo -->
<!--<a v-bind:href="hipervinculo()" target="_blank">
  {{ newItem == '' ? 'link' : newItem }}
</a>-->

<!-- Contador -->
<p class="counter">
    {{ characterCount }} / 200
  </p>

<!-- Agrupando en un div las entradas -->
<form v-on:submit.prevent="saveItem()" v-if="editing" class="add-item form">

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
    <button class="btn btn-primary" 
    :disabled="newItem.length === 0"
    > Guardar </button>
  
</form>
    <!-- Lista de items objetos-->
    <ul>
    <li
         v-for="({label, id, purchased, highPriority}, index) in reversedItems" 
         @click="togglePurchased(reversedItems[index])"
         :key="id"
         :class="{strikeout: purchased, priority: highPriority}"> 
         {{priority ? "🔥": "🛍️"}}
        {{label}} </li>
  </ul>
  
  <p v-if="items.length === 0"> 🥀NO HAY ELEMENTOS EN TU LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
