<template>
  <h1>Simple Button Vue</h1>
  <div class="animalBtn">
    <SimpleButtonWithProps animal="🐯" description="tiger" nutrition="🌮" @animal="reactToEvent($event)"></SimpleButtonWithProps>
    <SimpleButtonWithProps @animal="reactToEvent($event)"></SimpleButtonWithProps>
  </div>
  <p> currentFoodValue : {{currentFoodValue}} </p>
</template>

<script setup lang="ts">
import SimpleButtonWithProps from './components/SimpleButtonWithProps.vue'
import {ref} from "vue";

const currentFoodValue = ref();

function reactToEvent(payload: string){
  console.log('this is my payload', payload)
  currentFoodValue.value = payload;
}

</script>

<style scoped>
.animalBtn{
  display: flex;
  gap: 1rem;
}


</style>
