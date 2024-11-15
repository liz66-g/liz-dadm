 <script>
import { ref } from 'vue';
import planItem from './PlanPickerItem.vue';
//referencia reactiva para almacenar el plan seleccionado 
const selectedPlan = ref(null);
const plans = ref(['El cafetero','El chelero','El intelectual']);
const selectPlan=(name) =>{
  //Almacenar 
  selectPlan.value=name;
};
</script>

<template>
<div class="plans">
      <planItem v-for="plan in plans" :key="plan" :name="plan" 
      @select="(name)=>
      {console.log(name)}"/>
    </div> 
</template>
<div>

</div>

<script stup>

</script>

<style lang="scss" scoped>

</style>