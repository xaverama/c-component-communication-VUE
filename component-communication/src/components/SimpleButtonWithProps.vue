<template>
  <button id="feedBtn" @click="throwSomeFoodIntoTheCage">Feed Me! 🐼</button>
</template>

<script setup lang="ts">
import {computed, onMounted, ref} from "vue";

const hungryPanda = ref("🐼");
const food = ref("");
const bamboo = ref("🎋")
const pandaCage = computed(() => hungryPanda.value + food.value)

function throwSomeFoodIntoTheCage(){
  food.value = food.value + bamboo.value
  console.log("this is our panda cage", pandaCage.value)
}

onMounted(()=> {
  console.log("on page load panda cage", pandaCage.value)
})

</script>

<style scoped>

#feedBtn{
  background: palevioletred;
  border-radius: 8px;
  border: none;
  color: white;
  padding: 10px 20px;
}
#feedBtn:hover{
  opacity: 0.7;
  cursor: pointer;
}

</style>
