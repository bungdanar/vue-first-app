<script lang="ts">
import type { Friend } from '@/App.vue'
import { defineComponent, type PropType } from 'vue'

export default defineComponent({
  props: {
    friend: {
      type: Object as PropType<Friend>,
      required: true,
    },
  },
  data() {
    return {
      detailsAreVisible: false,
    }
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
  },
})
</script>

<template>
  <li>
    <h2>{{ friend.name }}</h2>
    <button @click="toggleDetails">{{ !detailsAreVisible ? 'Show' : 'Hide' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ friend.phone }}</li>
      <li><strong>Email:</strong> {{ friend.email }}</li>
    </ul>
  </li>
</template>

<style scoped></style>
