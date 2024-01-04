<script setup lang="ts">
import { useRouter } from 'vue-router'
const router = useRouter()

const props = defineProps({
  event: {
    type: Object,
    required: true,
  },
})

const register = () => {
  // If registration API call is successful
  // Push back to the event details
  router.push({
    name: 'EventDetails'
  })}
</script>

<template>
  <p>Register for event here</p>
  <button @click="register">Register Me!</button>
</template>
