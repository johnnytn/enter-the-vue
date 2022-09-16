<template>
  <div class="formsContainer">
    <div class="formQuantity">
      {{formQuantity}}
    </div>
    <div class="formContainer" v-for="(form, index) in forms" :key="index">
      <div class="formButtons">
        <label for="">
          Firsto Name:
          <input type="text" v-model="form.firstName" />
        </label>
        
        <label for="">
          Last Name:
          <input type="text" v-model="form.lastName" />
        </label>
      </div>
      <div v-if="form.firstName && form.lastName">
        <b>Full name:</b> {{ getFullName(form) }}
      </div>
  
      <button @click="() => onSubmit(form)" :disabled="!form.firstName || !form.lastName">
        {{ buttonTitle }}
      </button>
      
    </div>
    <br />
    <br />
    <button @click="addForm">Add form</button>
  </div>
</template>

<script>
export default {
  // props: ['propA', 'buttonTitle'],
  props: {
    propA: Number,
    buttonTitle: {
      type: String,
      default: "Submit",
      required: false,
    },
  },
  data() {
    return {
      forms: [{
        firstName: "",
      lastName: "",
      }],      
    }
  },
  computed: {
    formQuantity() {
      return `Quantidade de forms: ${this.forms.length}`
    },
  },
  watch:{
    counter(oldVal, newVal)  {
      console.log({oldVal})
      console.log({newVal})
    }
  },
  methods: {
    addForm() {
      const cleanForm = {firstName: "",
      lastName: "",}
      this.forms.push(cleanForm)

    },
    onSubmit(form) {
      this.$emit("submit-form", this.getFullName(form))
    },
    getFullName({firstName, lastName}) { 
      return `${firstName} ${lastName}`
    }
  },
}
</script>

<style>
.formsContainer {
  padding: 20px;
  border: 2px solid #cccc;
  border-radius: 5px
}
.formContainer {
  margin: 10px;
  padding: 10px;
  border: 2px solid #cccc;
  border-radius: 5px;  
}
.formButtons {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(156px, max-content));
  grid-gap: 16px;
}
.formQuantity {
  font-weight: bold;
}
</style>
