<script setup>
import { ref, onMounted } from 'vue'
import Demo from './components/Demo.vue';
const count = ref(0);
function increment() {
  count.value++;
  console.log(`The current count is ${count.value}.`)

}
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Composition API Counter</button>
  <p>count is: {{ count }}</p>
  <Demo />
</template>

<style scoped></style>
