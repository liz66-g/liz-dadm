<script setup>
import PlanPickerItem from './PlanPickerItem.vue';
import {ref, onMounted, onUnmounted} from 'vue';
/*Creando una variable reactiva para 
almacenar el plan seleccionado*/
const selectedPlan = ref(null);

const plans= ref(['El cafetero', 'El chelero', 'El intelectual']);
const selectPLan = (name) => {
  //alamecenar el plan almacenado
  selectedPlan.value = name; 
      };

const plansWrapper = ref(null);
//intentando obtener la referencia al elemento .plans
console.log("termina de ejecutar el scrip setup");

 //intentando obtener la referencia al elemento .plans
 onMounted(() => {
  console.log("El componente PlanPicker fue montado 😎");
  console.log(plansWrapper.value);
 })
 //registrando el hook mounted
onUnmounted(()=>{
  console.log("El componente PlanPicker se ha desmontado");
 })
</script>
 
<template>
    <div ref="plansWrapper" class="plans">
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