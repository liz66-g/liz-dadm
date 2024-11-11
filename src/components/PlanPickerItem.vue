<template>
<div @:click="selectPlan" class="plan">
    <div class="description">
      <span class="title"> {{ name }} {{selected ? '✨':''}}</span>
    </div>
  
  </div>
</template>

<script setup>
import {ref} from 'vue';
//Usando un macro para
//defenir las props
//const props = defineProps(['name','planIcon']);
const props =defineProps({
    name: {
      type: String,
      required: true
    }
  });
//definimos un evento
const emit = defineEmits(['select']);
  //variable que permite que el plan ha sido seleccionado 
  const selected = ref(false);
  //funcion que permite
  const selectPlan = () => {
    selected.value =true;
  }
  selected.value=true;
  //emitir
  //
  emit('select',props.name)
  const selectPlan=(name)=>{console.log(name)}
</script>

<style scoped>

</style>