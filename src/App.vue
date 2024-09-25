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
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
    </h1>
    <ul>
        <li
         v-for="{label, id} in items" :key="id"> {{label}} </li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 2rem;
}
</style>
