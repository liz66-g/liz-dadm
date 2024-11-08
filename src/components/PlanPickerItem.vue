<template>
  <div class="plan">

    <div class="description">
      
      <span class="title">
       {{ name }}
      </span>
    
    </div>
  
  </div>
</template>

<script setup>
//Usando un macro para
//defenir las props
//const props = defineProps(['name','planIcon']);
defineProps({
    name: {
      type: String,
      required: true
    }
  });
</script>

<style scoped>

</style>