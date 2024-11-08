<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref} from 'vue';
const plans= ref(['El cafetero', 'El chelero', 'El intelectual']);
</script>

<template>
    <div class="plans">
      <PlanPickerItem v-for="plan in plans" :key="plan" :name="plan" />
    </div>
</template>

<style scoped>

</style>