<script>
import { ref } from 'vue';
import planItem from './PlanPickerItem.vue';
const plans = ref(['El cafetero','El chelero','El intelectual']);
</script>

<template>
<div class="plans">
      <planItem v-for="plan in plans" :key="plan" :name="plan"/>
    </div> 
</template>
<div>

</div>

<script stup>

</script>

<style lang="scss" scoped>

</style>