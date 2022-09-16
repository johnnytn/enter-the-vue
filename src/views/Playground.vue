<template>
  <main>
    <div class="titleContainer">
      <span class="title">{{ title }}</span>
    </div>
    <button @click="increment">Count is: {{ count }}</button>
    <div v-if="count >= 10">
      <br />
      <h1>Vue is awesome!</h1>
      <button @click="decrement">Decrease!</button>
    </div>
    <br/>
    <br/>

    <MyFormsVue @submit-form="handleSubmit" :buttonTitle="buttonTitle" />
    <!-- <MyFormsVue @submit-form="handleSubmit" button-title="Submit!" />
    <my-form-vue @submit-form="handleSubmit" buttonTitle="Enviar" /> -->
  </main>
</template>

<script>
import MyFormsVue from "../components/MyForms.vue"

export default {
  data() {
    return {
      count: 0,
      title: "",
      buttonTitle: "Enviar",
    }
  },
  components: { MyFormsVue },
  created() {
    this.title = "Meu titulo"
  },
  // Lifecycle hooks
  // This function will be called when the component is mounted.
  mounted() {
    console.log(`The initial count is ${this.count}.`)
  },
  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    },
    handleSubmit(val) {
      alert(val)
    },
  },
}
</script>

<style>
.title {
  font-size: 26px;
  padding-bottom: 10px;
}
.titleContainer {
  padding-bottom: 20px;
  
}
</style>
