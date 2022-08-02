

<template>
  <button id="feedBtn" @click="throwSomeFoodIntoTheBowl">Feed Me! {{ props.animal }}</button>
</template>

<script setup lang="ts">
import {computed, onMounted, ref} from "vue";

const props = withDefaults(defineProps<{
  animal?: string;
  description?: string;
  nutrition?: string;
}>(), {
  animal: "🐼",
  description: "panda",
  nutrition: "🎋"
})

const emits = defineEmits<{
  (event: "animal", value: string): void
}>();

const hungryAnimal = ref(props.animal);
const foodBowl = ref("");
const food = ref(props.nutrition)
const animalCage = computed(() => hungryAnimal.value + foodBowl.value)

function throwSomeFoodIntoTheBowl() {
  foodBowl.value = foodBowl.value + food.value
  console.log(`this is our ${props.description} cage`, animalCage.value)
  emits("animal", foodBowl.value)
}

onMounted(() => {
  console.log(`on page load ${props.description} cage`, animalCage.value)
})

</script>

<style scoped>

#feedBtn {
  background: palevioletred;
  border-radius: 8px;
  border: none;
  color: white;
  padding: 10px 20px;
}

#feedBtn:hover {
  opacity: 0.7;
  cursor: pointer;
}

</style>
