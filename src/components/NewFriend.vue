<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  emits: ['add-contact'],
  data(){
    return {
      enteredName: '',
      enteredPhone: '',
      enteredEmail: ''
    }
  },
  methods: {
    sumbitData(){
      this.$emit('add-contact', this.enteredName,this.enteredPhone, this.enteredEmail)
    }
  }
})
</script>

<template>
<form @submit.prevent="sumbitData">
  <div>
    <label>Name</label>
    <input type="text" v-model="enteredName"/>
  </div>
  <div>
    <label>Phone</label>
    <input type="tel" v-model="enteredPhone"/>
  </div>
  <div>
    <label>E-Mail</label>
    <input type="email" v-model="enteredEmail"/>
  </div>
  <div>
    <button>Add contact</button>
  </div>
</form>
</template>

<style scoped></style>
