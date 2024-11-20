<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref, mounted} from 'vue';
/*Creando una variable reactiva para 
almacenar el plan seleccionado*/
const selectedPlan = ref(null);

const plans= ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPLan = (name) => {
  //alamecenar el plan almacenado
  selectedPlan.value = name; 
      };

 //intentando obtener la referencia al elemento .plans
 onMounted(() => {
  console.log("El componente PlanPicker fue montado 😎");
  console.log(document.querySelector('.plans'));
 })
</script>
 
<template>
    <div class="plans">
      <PlanPickerItem 
      v-for="plan in plans" 
      :key="plan" 
      :name="plan" 
      @select="selectPLan" 
      :select-plan="selectedPlan"
      />
    </div>
</template>

<style scoped>

</style>