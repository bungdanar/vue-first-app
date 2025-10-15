<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props:{
    id: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    phoneNumber: {
      type: String,
      required: true
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFavorite:{
      type: Boolean,
      required: false,
      default: false,
    }
  },
  emits: ['toggle-favorite', 'delete-friend'],
  data() {
    return {
      detailsAreVisible: false,
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
    toggleFavorite() {
      // Now, the event name is strong typed
      this.$emit('toggle-favorite', this.id)
    },
  },
})
</script>

<template>
  <li>
    <h2>{{ name }} {{ isFavorite  ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ !detailsAreVisible ? 'Show' : 'Hide' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete-friend', id)">Delete</button>
  </li>
</template>

<style scoped></style>
