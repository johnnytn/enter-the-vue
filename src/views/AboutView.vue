<template>
  <div class="about">
    <h1>{{ title }} {{ count }}</h1>
    <div>
      <span>{{ description }}</span>

      <button @click="increment">Increase!</button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue"

const title = "This is an about page"
const description = "loreal ipssum"
// reactive state
const count = ref(0)

const increment = () => {
  count.value++
}

onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
