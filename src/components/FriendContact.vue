<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  props: ['name', 'phone-number', 'emailAddress', 'isFavorite'],
  data() {
    return {
      detailsAreVisible: false,
      // Assign prop to local state
      friendIsFavorite: this.isFavorite,
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
    toggleFavorite() {
      // Modify state instead of prop
      if (this.friendIsFavorite === '1') {
        this.friendIsFavorite = '0'
      } else {
        this.friendIsFavorite = '1'
      }
    },
  },
})
</script>

<template>
  <li>
    <h2>{{ name }} {{ friendIsFavorite === '1' ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite">Toggle Favorite</button>
    <button @click="toggleDetails">{{ !detailsAreVisible ? 'Show' : 'Hide' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ ['phone-number'] }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<style scoped></style>
