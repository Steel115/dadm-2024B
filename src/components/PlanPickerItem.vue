<template>
  <div @:click="selectPlan" class="plan">

    <div class="description">
      
      <span class="title">{{ name }} {{ selected ? '✓' : '' }}</span>
    
    </div>
  
  </div>
</template>

<script setup>
//impor ref functio
import {ref} from 'vue';
//Usando un macro para
//defenir las props
//const props = defineProps(['name','planIcon']);
const props = defineProps({
    name: {
      type: String,
      required: true
    }
  });
  //Definir un evento (macro)
  const emit = defineEmits(['select']);
  //variable reactiva que permite recordar 
  // si el plan ha sido seleccionado
  const selected = ref(false);
  //funcion que permite cambiar el estado de la variable
  const selectPlan = () => {
    selected.value =true;
    //emitir un evento de que el
    //plan ha sido seleccionado
    emit('select', props.name);
  }
</script>

<style scoped>

</style>