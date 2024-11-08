<script setup>
import planItem from './components/PlanPickerItem.vue';
import { ref } from 'vue';
import PlanPicker from './components/PlanPicker.vue';
const plans = ref(['cafe','chelero','intelectual']);
</script>

<template>
  <header>
    <div>
      <span id="logo">Liquid Gold Box</span>
      <img src="./assets/logo.png" alt="logo">
    </div>
  </header>

  <div class="content">
    <h1 class="title">Coffee Plans</h1>

    <h2 class="subtitle">
      Viajamos por el mundo para encontrar el mejor café de origen único para ti
    </h2>
    <PlanPicker />
    

    <div class="plans">
      <planItem v-for="plan in plans" :key="plan" :name="plan"/>
    </div>
  </div>
</template>

<style scoped>
</style>