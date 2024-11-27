<script setup>
import PlanPicker from './components/PlanPicker.vue';
import { ref } from 'vue';
const showPlans = ref(false);
</script>

<template>
  <header>
    <div style="text-align: center;">
      <span id="logo">Itgam BOX EXPERIENCE</span><br>
      <img src="./assets/logo.png" alt="logo">
    </div>
  </header>

  <div class="content">
    <h1 class="title">Coffee Plans</h1>

    <h2 class="subtitle">
      Viajamos por el mundo para encontrar el mejor café de origen único para ti
    </h2>

    <labe><input type="checkbox" v-model="showPlans"> mostrar selector de planes </labe>

    <PlanPicker v-if="!showPlans"/>

    
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>