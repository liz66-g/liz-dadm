<template>
  <div @:click="selectPlan" class="plan">

    <div class="description">
      <span class="title">{{ name }} {{ isSelected ? '✓' : '' }}</span>
    </div>

  </div>
</template>

<script setup>
//importamos la funcion computed de vue para la propiedad computada
import { computed } from 'vue';

//defenir las props
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  selectPlan: String
});

//Definir un evento (macro)
const emit = defineEmits(['select']);
//funcion que permite cambiar el estado de la variable
const selectPlan = () => {
  //Emitir un evento de que el plan ha sido seleccionado 
  emit('select', props.name);
};

/*creando una propiedad computada. Para saber si el 
plan ha sido seleccionado */
const isSelected = computed(() => {
  return props.name === props.selectPlan;
});

</script>

<style scoped></style>