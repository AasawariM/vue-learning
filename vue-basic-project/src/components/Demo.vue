<template>
  <div>
    <button @click="increment">Option API Counter</button>
    <p>count is: {{ count }}</p>
  </div>
</template>


<script>
export default {
  data() {
    return {
      count: 0
    }
  },
  methods: {
    increment() {
      this.count++;
    }
  },
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  }
}
</script>
<style></style>